import random
from tkinter import *
from tkinter import messagebox
from tkinter import simpledialog


class BankAccountManagementSystem:
    def __init__(self, master):
        self.master = master
        self.master.title("Bank Account Management System")
        self.master.geometry("800x800")

        # Welcome message
        messagebox.showinfo("Welcome", "Welcome to Krishna Prasad Bank!")

        self.users = {}

        # Create Account Frame
        self.create_account_frame = Frame(self.master, bg='#F0F0F0')
        self.create_account_frame.pack(pady=20)

        # Labels
        self.name_label = Label(self.create_account_frame, text="Name:", font=('Arial', 12), bg='#F0F0F0')
        self.name_label.grid(row=0, column=0, padx=10, pady=10)

        self.age_label = Label(self.create_account_frame, text="Age:", font=('Arial', 12), bg='#F0F0F0')
        self.age_label.grid(row=1, column=0, padx=10, pady=10)

        self.mobile_label = Label(self.create_account_frame, text="Mobile:", font=('Arial', 12), bg='#F0F0F0')
        self.mobile_label.grid(row=2, column=0, padx=10, pady=10)

        self.dob_label = Label(self.create_account_frame, text="DOB (dd-mm-yyyy):", font=('Arial', 12), bg='#F0F0F0')
        self.dob_label.grid(row=3, column=0, padx=10, pady=10)

        self.pin_label = Label(self.create_account_frame, text="PIN:", font=('Arial', 12), bg='#F0F0F0')
        self.pin_label.grid(row=4, column=0, padx=10, pady=10)

        self.account_type_label = Label(self.create_account_frame, text="Account Type:", font=('Arial', 12), bg='#F0F0F0')
        self.account_type_label.grid(row=5, column=0, padx=10, pady=10)

        # Account type options
        self.account_type_var = StringVar(value="Savings")
        self.savings_radio = Radiobutton(self.create_account_frame, text="Savings", variable=self.account_type_var, value="Savings", bg='#F0F0F0')
        self.savings_radio.grid(row=5, column=1, padx=10, pady=5)

        self.current_radio = Radiobutton(self.create_account_frame, text="Current", variable=self.account_type_var, value="Current", bg='#F0F0F0')
        self.current_radio.grid(row=5, column=2, padx=10, pady=5)

        # Entries
        self.name_entry = Entry(self.create_account_frame, font=('Arial', 12), bg='#FFFFFF', relief='solid', borderwidth=1)
        self.name_entry.grid(row=0, column=1, padx=10, pady=10)

        self.age_entry = Entry(self.create_account_frame, font=('Arial', 12), bg='#FFFFFF', relief='solid', borderwidth=1)
        self.age_entry.grid(row=1, column=1, padx=10, pady=10)

        self.mobile_entry = Entry(self.create_account_frame, font=('Arial', 12), bg='#FFFFFF', relief='solid', borderwidth=1)
        self.mobile_entry.grid(row=2, column=1, padx=10, pady=10)

        self.dob_entry = Entry(self.create_account_frame, font=('Arial', 12), bg='#FFFFFF', relief='solid', borderwidth=1)
        self.dob_entry.grid(row=3, column=1, padx=10, pady=10)

        self.pin_entry = Entry(self.create_account_frame, show="*", font=('Arial', 12), bg='#FFFFFF', relief='solid', borderwidth=1)
        self.pin_entry.grid(row=4, column=1, padx=10, pady=10)

        # Create account button
        self.create_account_button = Button(self.create_account_frame, text="Create Account", font=('Arial', 12), bg='#4CAF50', fg='#FFFFFF', activebackground='#2E8B57', activeforeground='#FFFFFF', relief='raised', borderwidth=0, command=self.createAccount)
        self.create_account_button.grid(row=6, column=1, pady=20)

        # Login Frame
        self.login_frame = Frame(self.master, bg="#FFFFFF")
        self.login_frame.pack(pady=20)

        self.login_name_label = Label(self.login_frame, text="PIN:", font=("Arial", 14), bg="#FFFFFF")
        self.login_name_label.grid(row=0, column=0, padx=10, pady=10)

        self.login_pin_entry = Entry(self.login_frame, show="*", width=30, font=("Arial", 14))
        self.login_pin_entry.grid(row=0, column=1, padx=10, pady=10)

        self.login_button = Button(self.login_frame, text="Login", command=self.loginAccount, font=('Arial', 12), bg='#4CAF50', fg='#FFFFFF', activebackground='#2E8B57', activeforeground='#FFFFFF', relief='raised', borderwidth=0)
        self.login_button.grid(row=1, column=1, padx=10, pady=10)
        self.master.bind('<Return>', self.loginAccount)  # Allow login with "Enter" key

        # User Details Frame
        self.user_details_frame = Frame(self.master)

        # Labels
        label_style = {"fg": "green", "font": ("Calibri", 14)}

        self.name_label2 = Label(self.user_details_frame, text="Name:", **label_style)
        self.name_label2.grid(row=0, column=1, padx=10, pady=10)

        self.age_label2 = Label(self.user_details_frame, text="Age:", **label_style)
        self.age_label2.grid(row=1, column=1, padx=10, pady=10)

        self.mobile_label2 = Label(self.user_details_frame, text="Mobile:", **label_style)
        self.mobile_label2.grid(row=2, column=1, padx=10, pady=10)

        self.dob_label2 = Label(self.user_details_frame, text="DOB:", **label_style)
        self.dob_label2.grid(row=3, column=1, padx=10, pady=10)

        self.current_balance_label = Label(self.user_details_frame, text="Current Balance:", **label_style)
        self.current_balance_label.grid(row=4, column=1, padx=10, pady=10)

        # Buttons
        self.view_transaction_button = Button(self.user_details_frame, text="View Transaction Log", command=self.viewTransactionLogAccount, bg="green", fg="white")
        self.view_transaction_button.grid(row=5, column=0, padx=10, pady=10)

        self.deposit_button = Button(self.user_details_frame, text="Deposit", command=self.depositAccount, bg="yellow", fg="black")
        self.deposit_button.grid(row=5, column=1, padx=10, pady=10)

        self.withdraw_button = Button(self.user_details_frame, text="Withdraw", command=self.withdrawAccount, bg="orange", fg="white")
        self.withdraw_button.grid(row=5, column=2, padx=10, pady=10)

        self.logout_button = Button(self.user_details_frame, text="Logout", command=self.logoutAccount, bg="red", fg="white")
        self.logout_button.grid(row=5, column=3, padx=10, pady=10)

        # Initialize user data
        self.name = ""
        self.age = ""
        self.mobile = ""
        self.dob = ""
        self.pin = ""
        self.current_balance = 0
        self.transaction_log = []

    def generateOTP(self):
        otp = random.randint(1000, 9999)
        return otp

    def sendOTP(self, mobile):
        otp = self.generateOTP()
        messagebox.showinfo("OTP Sent", f"OTP sent to {mobile}: {otp}")
        return otp

    def createAccount(self):
        try:
            # Get user input
            name = self.name_entry.get()
            age = self.age_entry.get()
            mobile = self.mobile_entry.get()
            dob = self.dob_entry.get()
            pin = self.pin_entry.get()
            account_type = self.account_type_var.get()

            # Validate input
            if not name or not age or not mobile or not dob or not pin:
                messagebox.showerror("Error", "All fields are required!")
                return
            if not age.isdigit():
                messagebox.showerror("Error", "Age must be a number!")
                return
            if not pin.isdigit() or len(pin) != 4:
                messagebox.showerror("Error", "PIN must be a 4-digit number!")
                return

            # Initial deposit based on account type
            if account_type == "Savings":
                initial_deposit = 2000
            else:
                initial_deposit = 1000

            entered_initial_deposit = simpledialog.askinteger("Initial Deposit", f"Enter the initial deposit amount (minimum Amount is {initial_deposit}):")
            if entered_initial_deposit is None or entered_initial_deposit < initial_deposit:
                messagebox.showerror("Error", f"Minimum initial deposit for {account_type} account is {initial_deposit}!")
                return

            # Send OTP
            otp = self.sendOTP(mobile)
            entered_otp = simpledialog.askstring("OTP", "Enter the OTP sent to your mobile:")

            if str(otp) != entered_otp:
                messagebox.showerror("Error", "Invalid OTP!")
                return

            # Save user data
            self.name = name
            self.age = age
            self.mobile = mobile
            self.dob = dob
            self.pin = pin
            self.current_balance = entered_initial_deposit
            self.transaction_log = []

            # Add user data to dictionary
            self.users[pin] = {'name': name, 'age': age, 'mobile': mobile, 'dob': dob, 'balance': entered_initial_deposit, 'transaction_log': []}

            # Clear input fields
            self.name_entry.delete(0, END)
            self.age_entry.delete(0, END)
            self.mobile_entry.delete(0, END)
            self.dob_entry.delete(0, END)
            self.pin_entry.delete(0, END)

            # Thank you message
            messagebox.showinfo("Account Created", "Thank you for choosing Krishna Bank! Your account has been successfully created! Pleae login to show your details")
        except Exception as e:
            messagebox.showerror("Error", str(e))

    def loginAccount(self, event=None):
        try:
            pin = self.login_pin_entry.get()
            if pin in self.users:
                user_data = self.users[pin]
                self.name = user_data['name']
                self.age = user_data['age']
                self.mobile = user_data['mobile']
                self.dob = user_data['dob']
                self.current_balance = user_data['balance']
                self.transaction_log = user_data['transaction_log']

                self.login_frame.pack_forget()
                self.showUserDetails()
            else:
                messagebox.showerror("Login Error", "Incorrect PIN!")
        except Exception as e:
            messagebox.showerror("Error", str(e))

    def showUserDetails(self):
        self.user_details_frame.pack(pady=20)
        self.name_label2.config(text=f"Name: {self.name}")
        self.age_label2.config(text=f"Age: {self.age}")
        self.mobile_label2.config(text=f"Mobile: {self.mobile}")
        self.dob_label2.config(text=f"DOB: {self.dob}")
        self.current_balance_label.config(text=f"Current Balance: {self.current_balance}")

    def depositAccount(self):
        try:
            amount = simpledialog.askinteger("Deposit", "Enter deposit amount:")
            if amount and amount > 0:
                self.current_balance += amount
                self.transaction_log.append(f"Deposited: {amount}")
                messagebox.showinfo("Success", f"Deposited: {amount}")
                self.current_balance_label.config(text=f"Current Balance: {self.current_balance}")
            else:
                messagebox.showerror("Error", "Invalid amount!")
        except Exception as e:
            messagebox.showerror("Error", str(e))

    def withdrawAccount(self):
        try:
            amount = simpledialog.askinteger("Withdraw", "Enter withdrawal amount:")
            if amount and amount > 0 and amount <= self.current_balance:
                self.current_balance -= amount
                self.transaction_log.append(f"Withdrew: {amount}")
                messagebox.showinfo("Success", f"Withdrew: {amount}")
                self.current_balance_label.config(text=f"Current Balance: {self.current_balance}")
            else:
                messagebox.showerror("Error", "Invalid amount or insufficient balance!")
        except Exception as e:
            messagebox.showerror("Error", str(e))

    def viewTransactionLogAccount(self):
        try:
            log = "\n".join(self.transaction_log)
            if log:
                messagebox.showinfo("Transaction Log", log)
            else:
                messagebox.showinfo("Transaction Log", "No transactions yet.")
        except Exception as e:
            messagebox.showerror("Error", str(e))

    def logoutAccount(self):
        self.user_details_frame.pack_forget()
        self.login_frame.pack(pady=20)
        self.login_pin_entry.delete(0, END)


if __name__ == "__main__":
    root = Tk()
    app = BankAccountManagementSystem(root)
    root.mainloop()
