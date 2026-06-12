---
title: "[SOLVED] Changing device file permission at startup"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by tayran on 2008-01-20
Hi. I have been using kubuntu gutsy 64 on my acer aspire 5024 laptop for two months now. It is perfect as an 64 bit operating system and i can find quite bunch of help about installation problems because it is a rather old laptop. I have installed almost all functions properly instead of bluetooth. The bluetooth device itself is running via acer_acpi module but i had to activate it via this command every time:
sudo chmod 666 /proc/acpi/acer/bluetooth
echo 1 > /proc/acpi/acer/bluetooth (echo 0 to deactivate)

i couldn't have my bluetooth key in front work automatically. Even a key code was not defined for it so i decided to do it manually. First i have installed xbindkeys to handle key events. Then put this script to $HOME/.kde/Autostart to start at login:
sudo setkeycodes e058 200  #bluetooth off->on
sudo setkeycodes e057 201  #bluetooth on->off
xbindkeys & 

I have adjusted .xbindkeysrc config file according to key codes above adding these lines:
# bluetooth off->on
"echo 1 > /proc/acpi/acer/bluetooth"
  m:0x0 + c:168

# bluetooth on->off
"echo 0 > /proc/acpi/acer/bluetooth"
  m:0x0 + c:169

Now i can toggle bluetooth with bluetooth key. But still i have to run this command before using:
sudo chmod 666 /proc/acpi/acer/bluetooth

Since it is system device file ever time i reboot the system /proc/acpi/acer/bluetooth file is recreated with 644 properties so as a user i cannot write to it. So i put that command to bootup, tried run level 2-5 but i couldn't make it run run properly. When i login and check the file i see its attributes 644. Does anyone suggest a solution?

---

### Post by jeffus_il on 2008-01-20
Udev is the way to go, does this thread help:
[http://ubuntuforums.org/showthread.php?t=65497](http://ubuntuforums.org/showthread.php?t=65497)

---

### Post by banewman on 2008-01-20
Silly question first - have you checked in "users and groups" to see if your user is allowed to access bluetooth?
You can right a script for that at startup that'll just leave you with entering your password - here's how I'd do it
```
#!/bin/bash
sleep 5
$ (sudo chmod 666 /proc/acpi/acer/bluetooth)

```
at boot you"ll get a terminal that'll need a password - can't help more than that - sorry
:)

---

### Post by tayran on 2008-01-21
I have done everything from begining and i can use my bluetooth button in front panel. Thanks for the help. I think i have overlooked something.
 My first mistake was to include sudo commands in kde autostart which needs root password thus cannot be run automatically, 
I have placed an adjustbluetooth.sh file in /etc/init.d directory with this content:
#! /bin/sh
chmod 666 /proc/acpi/acer/bluetooth
setkeycodes e058 200 #this is kernel scan code and key code for key on
setkeycodes e057 201 #this is kernel scan code and key code for key off

Then created a symbolic link to it in /etc/rc2.d directory which contains run level 2 executables like this:
sudo ln -s /etc/init.d/adjustbluetooth.sh /etc/rc2.d/S99adjustbluetooth
Name starting with S99 provides that it is run after other scripts so that chmod is executed after file is created

Finally put xbindkeys program for handling key events to my local startup. 
Content of the .xbindkeysrc config file in my home dir is::
# bluetooth off->on
"echo 1 > /proc/acpi/acer/bluetooth"
m:0x0 + c:168 #this is xFree86 code for key on

# bluetooth on->off
"echo 0 > /proc/acpi/acer/bluetooth"
m:0x0 + c:169 #this is xFree86 code for key off

---

