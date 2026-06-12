---
title: "Blank desktop screen on boot"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by DominicC on 2013-01-27
Ok so, I have some experience with Ubuntu but not much. (I have been using it on a laptop for about a year)

Basically my dad asked me to install Ubuntu on to this ancient PC he got on Ebay. I ran some basic checks and the PC worked fine. (It even still had Windows XP installed.)

At first I tried to use the .exe to install Ubuntu alongside Windows. This appeared to work but upon selecting Ubuntu in the boot menu I was unable to select it and nothing happens.

Then I wiped the PC and replaced Windows with Ubuntu using a DVD. Now Ubuntu seemed to install correctly, but, when I restarted after the install I am taken to a blank desktop. (Not a blank screen, just a desktop without the sidebars)

There are no error messages and I can even right-click and create new folders, but the main Unity sidebar is missing and so is the bar at the top.

I did a Google search but couldn't seem to find anything similar.

Anyone know why this happens/How to fix it? I can post the hardware specs if needed.

---

### Post by bogan on 2013-01-27
Hi!, **DominicC,**

If this is ubuntu 12.10:
Right Click in the Desktop>Change Desktop Background> All Settings>Software Sources> Additional Drivers Tab.
Activate Video driver. Reboot

If that does not work, try 'Ctrl+Alt+F1', that should give a TTY, Text Terminal, and a login prompt. Enter your username and press 'Enter', then your password - it will not show & 'Enter'.

Post the output of: ```
uname -r
lspci -nnk | grep -iA3 vga
startx
``` and explain how far things get for more instructions.

[ If necessary 'Ctrl+Alt+F7'should return you to the GUI screen.]

Chao!, **bogan.**

---

### Post by ACubed10 on 2013-01-27
Hmm will this work with 12.04. When I install it I get to the desktop. No window managers but can right click and get a menu. Might try this. 12.10 work out of box with my graphics card but I prefer to stay LTS

---

### Post by bogan on 2013-01-28
Hi!, **ACubed 1**0,

I can not access 12.04 at the moment, but I think it will work there. 

Just that Additional Drivers in 12.04, has its own Icon in System Settings, and is not a Tab within Software Sources.

Chao!. **bogan.**

---

### Post by DominicC on 2013-01-28
> **bogan said:**
> Hi!, **DominicC,**

If this is ubuntu 12.10:
Right Click in the Desktop>Change Desktop Background> All Settings>Software Sources> Additional Drivers Tab.
Activate Video driver. Reboot

If that does not work, try 'Ctrl+Alt+F1', that should give a TTY, Text Terminal, and a login prompt. Enter your username and press 'Enter', then your password - it will not show & 'Enter'.

Post the output of: ```
uname -r
lspci -nnk | grep -iA3 vga
startx
``` and explain how far things get for more instructions.

[ If necessary 'Ctrl+Alt+F7'should return you to the GUI screen.]

Chao!, **bogan.**

I did what you first said and now it works fine, thanks. :)

---

### Post by worcesterman on 2013-02-21
I have a similar problem  with 12.04.2 LTS BUT I cannot login to the TTY screen either- it comes up with buffer I/O error. This has been a blocking problem now for 2 months. At least I still have Windoze!
Can anyone tell me how to do a clean reinstall without damaging the windows installation on my dual boot system.
Talking locally to others who have experienced the same problem- wipe and start again seems to be the only way forward.
Any bright ideas?

Worcesterman

---

### Post by bogan on 2013-02-21
Hi!, **worcesterman,**

There should be no difficulty, I have done dozens of Ubuntu installs on computers running Windows without problems. However, if you have a Uefi non-Bios system there may be complications, but I have no experience with that.

It depends, of course on whether you use a  'Wubi' system or a straight install. If the former, delete Ubuntu as you would any other Windows program and reinstall.

If the latter, make sure you know which partitions are used for '/root', '/home' & swap, then from the LiveCD/USB  install, choose the 'Something Else' option; make sure you do not select the Format whole drive option.

Chao!, **bogan.**

---

