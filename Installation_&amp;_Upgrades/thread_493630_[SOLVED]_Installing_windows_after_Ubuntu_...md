---
title: "[SOLVED] Installing windows after Ubuntu .."
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by subzero_acj on 2007-07-05
~

i have Ubuntu feisty in my primary partition. i wud like 2 install Windows. But when i boot frm windows cd it says it needs to write something to the primary drive, which contains windows incompatible contents. so it askd me to format the primary drive where i have installed Ubuntu. 

is there any way to solve this problem and install windows.

---

### Post by ubuntu.daemon on 2007-07-05
yeah so you noticed, windows likes to be the only thing on the drive, or so it thinks....
I would back up your important feisty stuff, delete ubuntu then install windows.  BUT Windows likes to install its **** all over the place....  So get a knoppix live-cd, and theres a program called QT-parted on it, so after you do your windows install, pop in the disc, reboot, jump on qtparted, and resize your windows to whatever size you may wish, it will freak on when you get back onto windows, it will do a disk check and thats all.  Ten you are free to use the rest of you drive for ubuntu yay!
:popcorn:

FYI! you cant just install qt-parted bc you cant resize the drive you are running the prpgram from hence the live-cd

---

### Post by subzero_acj on 2007-07-06
cool.... does Gparted work the same way ??

---

