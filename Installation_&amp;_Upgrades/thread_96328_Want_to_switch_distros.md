---
title: "Want to switch distros"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by cherokeecruiser on 2005-11-28
[FONT="Comic Sans MS"][/FONT]
[SIZE="3"][/SIZE]
I installed Linspire 5.0 two month ago but really haven't been impressed with the applications that were included.  I tried the Ubuntu 5.10 Live CD and think they included a great assortment of applications.  I am running a dual-boot with XP on two seperate SATA drives (XP on sda and Linspire on sdb) and have GRUB load XP by default.  My question is - if I want to get rid of Linspire and install Ubuntu will the installation program offer this option or will it try to put Ubuntu on an unused partition of sdb (I have two).  Basically I am not interested in keeping Linspire, but want to retain my Grub settings for XP to boot by default. Thanks in advance for any help you can offer!:D 

CherokeeCruiser

---

### Post by Leif on 2005-11-28
during installation, I think ubuntu will by default try to place nice and install to empty space. you can choose manual install, delete the space used by linspire (it'll be the partitions that are not NTFS or FAT32), and then tell ubuntu to automatically assign the space.

grub will be reinstalled, and will contain an entry for your windows installation.

---

### Post by aysiu on 2005-11-28
During installation, when you get to the partitioning part, select "Manually edit the partition table."

Then, find your former Linspire partition and select it.
For format, select "format as Ext3"
For mount point, select "/"

Install Grub to the MBR--it'll add Windows to the boot menu.

---

### Post by cherokeecruiser on 2005-11-28
Thanks for the responses.  I am going to try this next week after my final exams!  I have been impressed with what Ubuntu has to offer so far.

CherokeeCruiser

---

