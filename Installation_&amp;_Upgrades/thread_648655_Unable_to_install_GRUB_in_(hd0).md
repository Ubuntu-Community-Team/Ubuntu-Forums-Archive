---
title: "Unable to install GRUB in (hd0)"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by Xm4st3r on 2007-12-23
Aight...I had KUbuntu installed previous to this install. I formated a while ago and now im moving on Ubuntu. So here's my problem. My 320gb is partitioned this way
> /dev/sda1 = Windows XP (40Gb)
/dev/sda5 = I want to install Ubuntu on this one (40Gb)
/dev/sda6 = Its NTFS formated, all my stuff (games, programs, etc..) under WindowsXP are under this partition (234Gb)
/dev/sda7 = I want to use it as my swap (2Gb)

I set my /dev/sda5 as "/" and my /dev/sda7 as "swap"

My HDD was partitioned the same way back when I was using Kubuntu and I never had a single problem installing it.

But now for some reasons when I try to install Ubuntu, near the end I have a window popping saying 
> grub-install' (hd0) failed. This is a fatal error.

I'm trying a fresh install from a mailed install CD.

I'm a newbie when it comes to Ubuntu/Kubunt altogheter. So yeah...be as clear as possible.

---

### Post by logos34 on 2007-12-23
Boot from the live install cd.  

>Places>computer>click to mount ubuntu partition.

Open a terminal and type:

sudo fdisk -l

ls /media/disk/boot

ls /media/disk/boot/grub

cat /media/disk/boot/grub/menu.lst

Post it.  Maybe all that failed was writing grub to the mbr.

You could also just reinstall.  Doesn't take long and it might go right the second time.

---

