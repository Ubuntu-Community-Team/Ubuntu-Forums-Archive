---
title: "Bluetooth mouse losing connection in intrepid ibex"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kickabear on 2008-10-24
Okay, I'm going to try and be as detailed as I can.  

I had a fresh install of Hardy, which was working fine.  For some reason, I felt compelled to upgrade to Intrepid Ibex.  After a little work, I got everything working.  So far, so good.  I am really enjoying the changes and tweaks.

However, after the upgrade, I've begun having problems with my bluetooth mouse.  The bluetooth adapter is a Dell Wireless 355 Bluetooth, installed in a Dell Inspiron 9400 / e1705.  The mouse is a Logitech M-RBB93. Here are the details on what happens.

After upgrade, my mouse was working fine.  Then I rebooted.  After the reboot, the mouse wasn't working.  I went into Bluetooth Preferences, and saw that it was still listed as a known device.  But, it won't connect or pair, or whatever the word is.  So, I delete the device, then re-add it after pressing the Reset button on the bottom of the mouse.  After readd, it works great.  Okay, I thought it was solved.  

But, after the screensaver comes on, the bt mouse will not wake up the computer.  When I wake it up with the touchpad, the bt mouse is no longer responding.  I have to go back through deleting and re-adding it.  Also, after reboot, it fails to connect, and I have to re-add after that, too.

I completely uninstalled the Bluetooth software (Bluez, Bluetooth Support, Etc.), rebooted, reinstalled, rebooted and reconnected, but the results are the same.  

Does anyone have any advice?  I can post any information required.  Here is the output of lsusb:

john@minerva:~$ lsusb
Bus 005 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 005: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 005 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:9410 Alcor Micro Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
john@minerva:~$ 

Thanks!

---

### Post by kickabear on 2008-10-25
Okay, I discovered a fix.  I don't know if this is a good idea, but it solved my problem.  

In a terminal session, I executed the following command:

sudo gedit /etc/default/bluetooth

In the editor window which opens, I commented out the last two lines, like so:

#HID2HCI_ENABLED=1
#HID2HCI_UNDO=1

I rebooted, and my mouse was connected after reboot.  I haven't tested it by not moving it for a while, so I will do that now.  I suspect that the symptoms will be gone for me.  

Best of luck!
John

---

### Post by kickabear on 2008-10-25
Just to confirm, the change I describe above seems to have worked.  That is all.

---

### Post by jagdriver on 2008-10-27
Tried this and still no go.

The only way I got the mouse to reconnect was to undertake the fix found here [http://ubuntuforums.org/showthread.php?t=958048](http://ubuntuforums.org/showthread.php?t=958048)

---

### Post by jagdriver on 2008-10-27
I should say I did the above AND the fix found at [http://ubuntuforums.org/showthread.php?t=958048](http://ubuntuforums.org/showthread.php?t=958048)

---

