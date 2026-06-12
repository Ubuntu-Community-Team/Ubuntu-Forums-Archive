---
title: "Cricket Wireless A600 Broadband Modem&#8206;"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by joshuakimba on 2010-03-12
**Ok, I have loaded all the files, and I have run all the commands several times from the previous thread that instructs how to get linux to recognize the modem, but when I run the flipflop command this is what I get:**

COPYING                     flipflop.sh     usb_modeswitch-0.9.7
cricket_flip_amd64.deb      flipflop.sh~    usb_modeswitch.c
cricket_flip_i386.deb       Makefile        usb_modeswitch.conf
Cricket_Mode_Switch.tar.gz  README          usb_modeswitch.conf~
cricketum185c.sh            usb_modeswitch  usb_modeswitch.h
joshua@joshua-laptop:~/cricket/usb$ ^C
joshua@joshua-laptop:~/cricket/usb$ cd usb_modeswitch-0.9.7
joshua@joshua-laptop:~/cricket/usb/usb_modeswitch-0.9.7$ sudo ./flipflop.sh

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 Found default devices (1)
 Found a default device NOT in target class mode
Prepare switching, accessing device 002 on bus 003 ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x08 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye


 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Prepare switching, accessing device 003 on bus 003 ...
Resetting usb device .
 OK, device was reset
-> Run lsusb to note any changes. Bye

**My modem connects and then disconnects each time and then linux doesn't recognize it.**

---

### Post by collinge on 2010-03-12
Have you tried to remove the device and reinserting it?

---

### Post by joshuakimba on 2010-03-12
several times, plus, rebooting.

---

### Post by joshuakimba on 2010-03-12
I'll try hooking it up to my girlfriend's computer which has windows and installing whatever software that gets suggested. That is also on the previous thread. I actually made my laptop a pure linux machine.

---

### Post by joshuakimba on 2010-03-13
That did it, I answered my own question. For anyone also inquiring on this issue, if nothing else helps, plug your modem into a friend's computer with mac or windows. As soon as it connects the modem updates it's software. I do have to freaking reset my modem every few hours, but at least I can get I-net on the public transit now.

FYI: I also added a script at startup to save time. Keep in mind, you want to plug the modem in before the script kicks in:

Select:
System
Preferences
Startup Applications
Add

Then you can name the script and simply add the commands:
cd <directory that your flipflop file is in> |sudo ./flipflop.sh| <your admin password> |

The pipes are very important, but it will save you an annoying couple of steps each time you boot up.

---

