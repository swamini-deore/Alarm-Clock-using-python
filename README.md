Alarm-Clock-using-python


<img width="1918" height="1025" alt="image" src="https://github.com/user-attachments/assets/c6ae9d80-cfbb-4219-b54f-d59af94a1a84" />

⏰ Alarm Clock in Python is a simple project that lets users set alarms with a chosen time. It notifies with sound when the alarm rings. Built using Python with support for both command-line and GUI (Tkinter), this project demonstrates time handling, scheduling, and user interaction in Python. README.md

⏰ Alarm Clock – Python Project

📖 Overview

The Alarm Clock is a Python project that allows users to set alarms and receive notifications when the alarm time is reached.
It is implemented in both command-line and GUI (Tkinter) versions, making it beginner-friendly and practical.

🚀 Features

⏱️ Set custom alarm time (HH:MM:SS format).

🔔 Plays sound when alarm rings.

🖥️ Two versions:

CLI (command-line based).

GUI (Tkinter based).

🎓 Great for beginners to learn time handling, Tkinter, and libraries in Python.


🛠️ Tech Stack

Language: Python

Libraries:
datetime – Time handling

time – Waiting mechanism

playsound – Play alarm sound

tkinter – GUI version


📂 Project Structure
project/ │── alarm_clock.py # Command-line version │── alarm_clock_gui.py # Tkinter GUI version │── alarm.mp3 # Alarm sound file │── README.md

▶️ Usage
CLI Version
python alarm_clock.py


Enter alarm time in HH:MM:SS format → plays alarm sound when time matches.

GUI Version
python alarm_clock_gui.py


Set hours, minutes, seconds.

Click "Set Alarm" → alarm rings at given time.

📸 Example (GUI)

(Add screenshot of Tkinter window here if possible)

📜 License

This project is licensed under the MIT License – free to use and modify.


---

## 🔹 Sample Python Code  

### ✅ Command-line version  
```python
import datetime
import time
from playsound import playsound

alarm_time = input("Enter alarm time (HH:MM:SS): ")

while True:
    current_time = datetime.datetime.now().strftime("%H:%M:%S")
    if current_time == alarm_time:
        print("⏰ Alarm! Time to wake up!")
        playsound("alarm.mp3")
        break
    time.sleep(1)

✅ Tkinter GUI version
import datetime
import time
import threading
from tkinter import *
from playsound import playsound

def set_alarm():
    alarm_time = f"{hour.get()}:{minute.get()}:{second.get()}"
    print(f"Alarm set for {alarm_time}")
    threading.Thread(target=alarm, args=(alarm_time,), daemon=True).start()

def alarm(alarm_time):
    while True:
        current_time = datetime.datetime.now().strftime("%H:%M:%S")
        if current_time == alarm_time:
            print("⏰ Alarm! Time to wake up!")
            playsound("alarm.mp3")
            break
        time.sleep(1)

root = Tk()
root.title("Alarm Clock")

Label(root, text="Set Time (HH:MM:SS)", font=("Helvetica", 14)).pack(pady=10)

frame = Frame(root)
frame.pack()

hour = StringVar(root, "00")
minute = StringVar(root, "00")
second = StringVar(root, "00")

Entry(frame, textvariable=hour, width=3, font=("Helvetica", 18)).pack(side=LEFT)
Entry(frame, textvariable=minute, width=3, font=("Helvetica", 18)).pack(side=LEFT)
Entry(frame, textvariable=second, width=3, font=("Helvetica", 18)).pack(side=LEFT)

Button(root, text="Set Alarm", command=set_alarm, font=("Helvetica", 14)).pack(pady=20)

root.mainloop()
