---
title: "USB in Hoary Hedgehog"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by abajaj on 2005-11-12
HI Everyone,
I am using Ubuntu Hoary Hedgehog 5.04 on an IBM 390E laptop. 
It installs fine, and everything works great, including the printer. 
The only issue is: THe USB port on the aptop does not seem to read a memory stick (flash drive).
The memory sticks are fine, and are read on other windows laptops I have. 

My questions are:
1. How do I check to see if the USB port is OK in Ubuntu, without connecting a flash drive? 

2. For the flash drive to work, does it need some other kind of formatting on Ubuntu, or will a flash drive (memory stick that is) that works on windows machines work fine on Ubuntu without any problems?

thanks in advance for any help. 
-abajaj

---

### Post by aysiu on 2005-11-12
Hm. I'm not sure what's going on.

In theory, you shouldn't have to reformat the drive. I use an external hard drive that's FAT32 and an MP3 player that's FAT16, and they're both read perfectly fine from Ubuntu (Hoary *and* Breezy).

It sounds as if your gnome-volume-manager isn't working right. Just for kicks, though, when you have your flash drive plugged in, what's the output of this command ```
sudo fdisk -l
```? To open a terminal, go to Applications > Accessories > Terminal--that's where you type the command.

---

### Post by abajaj on 2005-11-17
Thanks. 
Just so you know, the USB jack used towork fine with windows, so it's not that the jack is disabled. 
WHen i plug in a memory stick, and do a sudo fdisk -l ,   I get:
Disk /dev/hda: 6495 MB, 6495068160 bytes
255 heads, 63 sectors/track, 789 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         753     6048441   83  Linux
/dev/hda2             754         789      289170    5  Extended
/dev/hda5             754         789      289138+  82  Linux swap / Solaris

So i don;t see the USB there at all. 
What should I do?
thanks
-abajaj

---

