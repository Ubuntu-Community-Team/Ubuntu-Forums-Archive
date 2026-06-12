---
title: "Troubles Installing Grub"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by b3n0 on 2007-05-29
Hey all, 

I currently have ubuntu as a virtual OS. I love it, I feel its time to properly install it. I have a 200gb SATA drive. I partitioned the drive so I could have windows on 170gb, 2mb of swap space and the remainder for ubuntu. The live CD works fine and is only right at the end of the installation that I get a bang saying that grub hasn’t installed properly. One of the options in the wizard is 'where would you like to install grub' I’ve tried HD0, HD1, SD0, SD1, each with no prevail. Ultimately I'd like to be able to select form either windows or ubuntu in the boot sequence. To do this I understand that grub must be installed on the primary partition.

Is there any way to find out the computer name (hd1, sd1) for the primary partition of the disk?
   

Thanks for your help,


Ben

---

### Post by RevNL on 2007-05-29
The boot loader should go on the boot drive, not a partition.  If:

sda1 = windows
sda3 = linux

Then Grub goes on 'sda'.

There's another way to set it up (possibly better) but that works for me.  Grub will start windows and linux.

---

