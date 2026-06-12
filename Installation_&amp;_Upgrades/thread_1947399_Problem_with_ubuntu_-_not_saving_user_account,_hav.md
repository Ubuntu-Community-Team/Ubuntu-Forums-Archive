---
title: "Problem with ubuntu - not saving user account, have to instal over and over again"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by cushpajz on 2012-03-26
Hello people. I have a problem. I have installed ubuntu 32bit on my virtual machine, and it worked fine, the problem starts when I, turn of my virtual pc and then turn it back on, I dont have my user account saved, and i need to Install all over again, if someone can give me tutorial how I can set up ubuntu to stay on my virtual machine all the time, I'll be thankfull. :)

---

### Post by winh8r on 2012-03-26
You need to ensure that the machine is not reading the .iso that you started it from. Make sure it is looking at the .vdi image which is where your installation is saved.

You should be able to select it from the settings menu of the virtual machine, before you start it up.It will be under "Storage"

---

### Post by cushpajz on 2012-03-26
So I need to install ubuntu first and then shut it down and read from just set to read from .vdi file? I dont need any shells or that..?

---

### Post by QIII on 2012-03-26
The .vdi is the virtual hard drive for the virtual machine.  When you start your virtual machine, do not keep the CD in the drive.  Just start the machine and it will use the virtual disk in exactly the same manner (virtually) as your physical machine boots with the physical hard drive.

---

### Post by cushpajz on 2012-03-26
Thanks it works! :)

---

### Post by liamhale on 2012-03-26
> **winh8r said:**
> You need to ensure that the machine is not reading the .iso that you started it from. Make sure it is looking at the .vdi image which is where your installation is saved.

You should be able to select it from the settings menu of the virtual machine, before you start it up.It will be under "Storage"
i have a smilar probem to this, i am not sure if it will make it work but i am willing to try, i have restarted my computer and i cannot find the settings menu, this was from startup, is this a option on ubuntu or should it be one command you can press as soon as you start up?

---

### Post by winh8r on 2012-03-26
When you open the virtual box application there is a list of available options "NEW" "SETTINGS" "START" "DISCARD".

You click on settings and then on storage in the left hand menu.

You will see your virtual machines name there with two storage options, now that you have installed it you need to select the .iso image and then click on the "-" symbol at the bottom of the window to remove it from the tree.
This will leave the .vdi image which is where the installation is kept (virtually).
After you have done this you can go back to the main menu and select "START" and your virtual machine will start up from the .vdi, and will be just like starting a "normal" operating system with a login window etc.

Hope this helps.

---

