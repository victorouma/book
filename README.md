
# book
class Superhero:
    def __init__(self, name, secret_identity, power_level):
        self.name = name
        self._secret_identity = secret_identity  # Protected attribute
        self.__power_level = power_level  # Private attribute
        
    def introduce(self):
        print(f"I am {self.name}! Power level: {self.get_power_level()}")
        
    def get_power_level(self):
        return self.__power_level
        
    def increase_power(self, amount):
        if amount > 0:
            self.__power_level += amount
            print(f"{self.name}'s power increased to {self.__power_level}!")
        else:
            print("Power increase must be positive!")
    
    def use_power(self):
        print(f"{self.name} uses a generic superhero power!")


class FlyingHero(Superhero):
    def __init__(self, name, secret_identity, power_level, max_altitude):
        super().__init__(name, secret_identity, power_level)
        self.max_altitude = max_altitude
        
    def use_power(self):  # Polymorphism - overriding parent method
        print(f"{self.name} soars through the air at {self.max_altitude} feet!")
        
    def aerial_attack(self):
        print(f"{self.name} performs a devastating dive bomb attack!")


class TechHero(Superhero):
    def __init__(self, name, secret_identity, power_level, gadget_count):
        super().__init__(name, secret_identity, power_level)
        self.gadget_count = gadget_count
        
    def use_power(self):  # Polymorphism - overriding parent method
        print(f"{self.name} deploys {self.gadget_count} advanced gadgets!")
        
    def invent_gadget(self):
        self.gadget_count += 1
        print(f"{self.name} created a new gadget! Total gadgets: {self.gadget_count}")


# Testing the classes
superman = FlyingHero("Superman", "Clark Kent", 95, 40000)
iron_man = TechHero("Iron Man", "Tony Stark", 88, 42)

superman.introduce()
superman.use_power()
superman.aerial_attack()

iron_man.introduce()
iron_man.use_power()
iron_man.invent_gadget()

# Encapsulation example
print(iron_man._secret_identity)  # Accessing protected attribute (convention)
# print(iron_man.__power_level)  # Would cause error - private attribute

class Animal:
    def __init__(self, name):
        self.name = name
        
    def move(self):
        print(f"{self.name} moves in a generic way")


class Fish(Animal):
    def move(self):
        print(f"{self.name} swims gracefully through the water 🐟")


class Bird(Animal):
    def move(self):
        print(f"{self.name} flies high in the sky 🦅")


class Snake(Animal):
    def move(self):
        print(f"{self.name} slithers silently across the ground 🐍")


class Kangaroo(Animal):
    def move(self):
        print(f"{self.name} hops powerfully with its strong legs 🦘")


# Create a list of animals
animals = [
    Fish("Nemo"),
    Bird("Eagle"),
    Snake("Viper"),
    Kangaroo("Joey")
]

# Demonstrate polymorphism
for animal in animals:
    animal.move()

print("\nSpecial movement demonstration:")
animals[1].move()  # Bird's movement
animals[3].move()  # Kangaroo's movement
