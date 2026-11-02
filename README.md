#Practical 1 Student marks report
```
name = input("Enter your Name: ")
reg_id = input("Enter your ID: ")
br = input("Enter Branch: ")

dbms = float(input("DBMS: "))
os = float(input("OS: "))
pdec = float(input("PDEC: "))
ai_ml = float(input("AI_ML: "))
dlca = float(input("DLCA: "))

total = dbms + os + pdec + ai_ml + dlca
ave = total / 5
per = total / 500 * 100

print(f"Your Name is {name}")
print(f"You scored {total} out of 500")
print(f"Average: {ave:.2f}")
print(f"Percentage: {per:.2f}%")
```
Practical 2 Number guessing game
```
import random as rd

secret_number = rd.randint(1, 50)
attempts = 0

while True:
    guess = int(input("Enter a number: "))
    attempts = attempts + 1

    if guess > secret_number:
        print("Too high!")
    elif guess < secret_number:
        print("Too low!")
    else:
        print("You guessed it!")
        print("Number of guesses:", attempts)
        break
```
Practical 3 rocl,paper,scissor
```
import random

choices = ["rock", "paper", "scissors"]
player_score = computer_score = 0

for _ in range(100):
    player = input("Choose rock, paper, or scissors: ").lower()
    computer = random.choice(choices)

    if player == computer:
        print("Draw")
    elif (player, computer) in [
        ("rock", "scissors"),
        ("paper", "rock"),
        ("scissors", "paper")
    ]:
        player_score += 1
        print("You win!")
    else:
        computer_score += 1
        print("Computer wins!")

    if player_score == 3 or computer_score == 3:
        break

if player_score == 3:
    print("You win the game!")
elif computer_score == 3:
    print("Computer wins the game!")
```
Practical 4 sentence analyzer
```
sentence = "Python is boring subject 404"
words = sentence.split()

vowels = consonants = digits = spaces = 0

for ch in sentence:
    if ch.lower() in "aeiou":
        vowels += 1
    elif ch.isalpha():
        consonants += 1
    elif ch.isdigit():
        digits += 1
    elif ch == " ":
        spaces += 1

print("Words:", len(words))
print("Vowels:", vowels)
print("Consonants:", consonants)
print("Digits:", digits)
print("Spaces:", spaces)
print("Longest word:", max(words, key=len))
```
Practical 5 student marks analysis
```
marks = []

for i in range(10):
    marks.append(int(input(f"Enter mark {i + 1}: ")))

def maximum(marks):
    highest = marks[0]
    for m in marks:
        if m > highest:
            highest = m
    return highest

average = sum(marks) // 10

above_avg = 0
for m in marks:
    if m > average:
        above_avg += 1

print("Highest:", maximum(marks))
print("Lowest:", min(marks))
print("Average:", average)
print("Above average:", above_avg)
print("Unique marks:", set(marks))
```
Practical 6 Shopping cart program
```
def total(price, qty):
    return price * qty

def cart_total():
    grand = 0
    for name in cart:
        grand += total(products[name], cart[name])
    return grand

products = {"Shirt": 350, "Mug": 150, "Badge": 50}
cart = {}
menu = ["View Products", "Add Item", "Update Item", "Remove Item", "Total Amount", "Show Bill", "Exit"]

while True:
    print("\n--- Shopping Cart ---")
    count = 1
    for option in menu:
        print(count, option)
        count += 1
    choice = int(input("Enter choice: "))

    if choice == 1:
        print("Products:")
        for name in products:
            print(name, "Rs", products[name])
    elif choice == 2:
        name = input("Product name: ").capitalize()
        if name in products:
            qty = int(input("Quantity: "))
            if name in cart:
                cart[name] += qty
            else:
                cart[name] = qty
            print("Item added")
        else:
            print("Product not found")
    elif choice == 3:
        name = input("Product name: ").capitalize()
        if name in cart:
            cart[name] = int(input("New quantity: "))
            print("Item updated")
        else:
            print("Item not in cart")
    elif choice == 4:
        name = input("Product name: ").capitalize()
        if name in cart:
            del cart[name]
            print("Item removed")
        else:
            print("Item not in cart")
    elif choice == 5:
        print("Total Amount: Rs", cart_total())
    elif choice == 6:
        if len(cart) == 0:
            print("Cart is empty")
        else:
            print("\n--- BILL ---")
            for name in cart:
                price = products[name]
                qty = cart[name]
                print(f"{name}: {qty} x {price} = {total(price, qty)}")
            print("----------------")
            print("Grand Total: Rs", cart_total())
    elif choice == 7:
        print("Thank you for shopping!")
        break
    else:
        print("Invalid choice")
     
```
Practical 7 contact book program
```
def add_contact(contacts):
    name = input("Enter name: ").capitalize()
    if name in contacts:
        print("Contact already exists")
    else:
        contacts[name] = input("Enter phone number: ")
        print("Contact added")

def search_contact(contacts):
    name = input("Enter name to search: ").capitalize()
    if name in contacts:
        print(name, "-", contacts[name])
    else:
        print("Contact not found")

def update_contact(contacts):
    name = input("Enter name to update: ").capitalize()
    if name in contacts:
        contacts[name] = input("Enter new phone number: ")
        print("Contact updated")
    else:
        print("Contact not found")

def delete_contact(contacts):
    name = input("Enter name to delete: ").capitalize()
    if name in contacts:
        del contacts[name]
        print("Contact deleted")
    else:
        print("Contact not found")

def display_contacts(contacts):
    if len(contacts) == 0:
        print("Contact book is empty")
    else:
        print("\n--- Contacts ---")
        for name in contacts:
            print(name, "-", contacts[name])

contacts = {}
while True:
    print("\n--- Contact Book ---")
    print("1. Add Contact")
    print("2. Search Contact")
    print("3. Update Contact")
    print("4. Delete Contact")
    print("5. Display All Contacts")
    print("6. Exit")
    choice = int(input("Enter choice: "))
    
    if choice == 1:
        add_contact(contacts)
    elif choice == 2:
        search_contact(contacts)
    elif choice == 3:
        update_contact(contacts)
    elif choice == 4:
        delete_contact(contacts)
    elif choice == 5:
        display_contacts(contacts)
    elif choice == 6:
        print("Goodbye!")
        break
    else:
        print("Invalid choice")
```
Practical 8 Factorial and fibonacci series
```
# Factorial - Iterative Method
number = int(input("Enter a number: "))
factorial = 1
if number < 0:
    print("Factorial is not defined for negative numbers")
else:
    for i in range(1, number + 1):
        factorial *= i
    print(f"Factorial of {number} is {factorial}")

# Factorial - Recursive Method
def factorial(number):
    if number == 0 or number == 1:
        return 1
    return number * factorial(number - 1)

num = int(input("Enter a number: "))
if num < 0:
    print("Factorial is not defined for negative numbers")
else:
    print(f"Factorial of {num} is {factorial(num)}")

# Fibonacci Series - Recursive Method
def fibonacci(number):
    if number == 0 or number == 1:
        return number
    return fibonacci(number - 1) + fibonacci(number - 2)

num = int(input("Enter a position: "))
if num < 0:
    print("Fibonacci is not defined for negative positions")
else:
    print(f"Fibonacci number at position {num} is {fibonacci(num)}")

# Fibonacci Series - Iterative Method
number = int(input("Enter a position: "))
if number < 0:
    print("Fibonacci is not defined for negative positions")
else:
    first = 0
    second = 1
    for i in range(number):
        third = first + second
        first = second
        second = third
    print(f"Fibonacci number at position {number} is {first}")
```
Practical 9 Bank acc program
```
class BankAccount:
    def __init__(self, acc_name, acc_no, bal=0.0):
        self.AccountName = acc_name
        self.AccountNumber = acc_no
        self.Balance = bal
        self.t_h = []

    def Deposite(self, amount):
        if amount <= 0:
            print("Invalid Amount")
        else:
            self.Balance += amount
            self.t_h.append(f"Deposit: {amount}")
            print("Amount Successfully Deposited")

    def withdrawal(self, amount):
        if amount > self.Balance:
            print("Insufficient Amount")
        elif amount <= 0:
            print("Invalid Amount")
        else:
            self.Balance -= amount
            self.t_h.append(f"Withdrawal: {amount}")
            print("Withdrawal Successful")

    def balance_inquiry(self):
        print(f"Account Holder: {self.AccountName}")
        print(f"Account Number: {self.AccountNumber}")
        print(f"Current Balance: {self.Balance}")

    def display_transactions(self):
        print("--- Transaction History ---")
        if len(self.t_h) == 0:
            print("No transactions yet.")
        else:
            for t in self.t_h:
                print(t)

acc = BankAccount("Mahir", "123456789", 10000)
acc.Deposite(5000)
acc.withdrawal(2000)
acc.balance_inquiry()
acc.display_transactions()
```
