---
title: "Ubuntu Slow after 7.04 to 7.10 upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by prof3ta on 2007-10-19
Hi everyone, I've just upgraded my Ubuntu but now the system is really slow.
In particular, I cannot fluently see videos on web, the screen image is slow to appear, the apt-get utility takes much more time than before to read the database and install/remove packets.
I reconfigured the xserver-xorg, with no changes.
I use a laptop ASUS L3355M (2500+ Athlon XP, 512 RAM, Sis graphical chipsets, no DRI)

Prof3ta
[http://prof3ta.netsons.org](http://prof3ta.netsons.org)

---

### Post by prof3ta on 2007-10-19
I found the reason of the problem.
In the new kernel (2.6.22) the module for my IDE HDD (sis5513) was apparently subsituted by the pata_sis one, which was not able to automatically set the DMA access ON for the hard drive. Maybe this is connected with the passage from hda to sda naming for hdds in the new kernel.
Hdparam helped to fix the problem.

---

### Post by exile on 2007-10-19
I've also noticed that upgrading to 7.10 seemed to be a step backwards speed-wise for me. I will try your solution. Thanks!

---

### Post by monkeybrain on 2007-10-22
prof3ta, would it be possible for you to give me more details of how you fixed your problem. I have an old Asus M2400E laptop with Sis graphics and it too is now extremely slow (opening applications, scrolling etc.). The fan is also constantly on full speed now. I should note I'm running Xubuntu and I'm a Linux newbie.

At first I thought it was the graphics driver, which was set to some default one rather than a sis one. I managed to fix that but problems continue.

---

### Post by radioman1000 on 2007-10-23
hda was not being recognized after an upgrade from update manager

this worked for me

in a terminal console:

sudo apt-get update
sudo apt-get upgrade


then reboot

---

### Post by kaarelkk on 2008-04-07
It also worked for me. After doing that and one reboot, my linux went crazy.. different skinn and some errors, but after the second reboot, it was all fine and fast again. Thanx alot.

---

### Post by kaarelkk on 2008-04-08
> **kaarelkk said:**
> It also worked for me. After doing that and one reboot, my linux went crazy.. different skinn and some errors, but after the second reboot, it was all fine and fast again. Thanx alot.

Edit: After an other reboot I notice, that the system is somewhat fast when I have extra visual effects turned on. If I put it to now effects, the system is very slow again: programs pop up really slowly after I launch them, If typing in firefox, letters pop up in an interval of 1.5 second. and buttons are laggy. I also noticed that my keyboard layout is changed to english again - should be Estonian layout. 

I have Intel P4 3.0Ghz 
Ati Radeon 9550
1280mb Ram

If anyone could help how to get rid of the lag and those problems, It would be great. 
(PS! I am pretty new to linux and ubuntu)

---

