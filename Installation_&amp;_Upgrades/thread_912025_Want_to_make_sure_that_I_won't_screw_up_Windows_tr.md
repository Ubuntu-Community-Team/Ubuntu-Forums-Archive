---
title: "Want to make sure that I won't screw up Windows trying to install Ubuntu"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by FunPika on 2008-09-06
I'm afraid of messing up Windows completely while installing Ubuntu, so I decided I should post what I intend to do before actually installing (I have looked at all the steps in the installer already and am now posting while booted into Windows). 

1. I am going to resize my Windows partition while in Windows (probably going to make it around 21 gigabytes smaller).
2. Once I boot up the Live CD I am going to start the installer, answer the first 3 questions then move on to MANUALLY creating the Ubuntu partitions. 
3. In the manual table editor I will first make a Swap partition with 1 gigabyte of space. 
4. Then I will make a Root partition (ext3 format and logical partition) with 10 gigabytes of space.
5. I will make a Home partition (once again ext3 and logical partition) with 10 gigabytes of space. 
6. I will enter computer/account information then import My Pictures, User Picture, Wallpaper, and Firefox settings from my Windows account. 
7. The installation will be finalized. 

Notes: My computer is currently running XP Home SP3, has a stupid recovery partition instead of a DVD, and already has GRUB bootloader installed from a Wubi installation I uninstalled.

---

### Post by zvacet on 2008-09-06
You don´t have to worry about messing Windows if you install Ubuntu on unallocated space.Your plan look good but I will install partitions in this order;root,home,swap.But that is really optional.You can read [this]("http://psychocats.s465.sureserver.com/ubuntu/installing") as instruction.

---

### Post by Sef on 2008-09-06
What you want to do is fine.  All should work out well for you.

---

