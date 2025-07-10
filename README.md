# MITMA

# check_passwords.py

def load_breached_passwords(file_path):
    try:
        with open(file_path, 'r') as file:
            return set(line.strip() for line in file)
    except FileNotFoundError:
        print(f"Error: File '{file_path}' not found.")
        return set()

def check_password(password, breached_passwords):
    if password in breached_passwords:
        print("⚠️  Warning: This password has been breached before. Choose a different one.")
    else:
        print("✅ This password has not been found in known breaches.")

def main():
    breached_file = 'breached_passwords.txt'
    breached_passwords = load_breached_passwords(breached_file)

    while True:
        user_input = input("Enter a password to check (or type 'exit' to quit): ")
        if user_input.lower() == 'exit':
            break
        check_password(user_input, breached_passwords)

if __name__ == "__main__":
    main()
