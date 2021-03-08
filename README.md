# Coffee-machine-simulater-
a programme that mimics a real life coffee machine 

MENU = {
    "espresso": {
        "ingredients": {
            "water": 50,
            "coffee": 18,
        },
        "cost": 1.5,
    },
    "latte": {
        "ingredients": {
            "water": 200,
            "milk": 150,
            "coffee": 24,
        },
        "cost": 2.5,
    },
    "cappuccino": {
        "ingredients": {
            "water": 250,
            "milk": 100,
            "coffee": 24,
        },
        "cost": 3.0,
    }
}

resources = {
    "water": 300,
    "milk": 200,
    "coffee": 100,
}


profit = 0


def check_resources(order_ingredients):
    for item in order_ingredients:
        if order_ingredients[item] >= resources[item] :
            print(f"Sorry there is not enough {item}")
            return False
    return True

def process_coins():
    """ Returns the total calcualted from coins entered   """
    print("PLease insert coins. ")
    total = int(input(" how many 50p ? : ")) *0.50
    total += int(input(" how many 20p ? : ")) *0.20
    total += int(input(" how many 10p ? : ")) *0.10
    total += int(input(" how many 5p ? : ")) *0.05
    return total

def transaction_successful(payment, drink_cost):
    """ Retyrns True if payment is accepted or False if money is insufficient """
    if payment >= drink_cost:
        change = round(payment - drink_cost, 2)
        print(f"here is ${change} in change.")
        global profit
        profit += drink_cost
        return True
    else:
        print("sorry not enough money")
        return False


def make_coffee(drink_name, order_ingredients):
    """Dedeuct the required ingredients from the resources. """
    for item in order_ingredients:
        resources[item] -= order_ingredients[item]
    print(f" Here is your {drink_name}")
