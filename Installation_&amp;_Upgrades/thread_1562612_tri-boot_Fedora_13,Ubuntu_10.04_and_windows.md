---
title: "tri-boot Fedora 13,Ubuntu 10.04 and windows"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by ultimatelinux on 2010-08-27
this is the output of sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf623f623

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3917    31457280    7  HPFS/NTFS     **windows resides here**
/dev/sda2            3917        4166     1999872   82  Linux swap / Solaris     **swap for Ubuntu**
/dev/sda3            7056       19458    99614720    7  HPFS/NTFS      **NTFS partition with data**
/dev/sda4            4166        7056    23216128   83  Linux         ** Ubuntu's /**

**now I want to install fedora 13 in /dev/sda3,what should I do?**

---

### Post by presence1960 on 2010-08-27
before giving any advice, what version of ubuntu are you running?

---

### Post by ultimatelinux on 2010-08-29
> **presence1960 said:**
> before giving any advice, what version of ubuntu are you running?
I think that can learned from thread title.

---

### Post by leucippus on 2010-08-29
Tread lightly...

 I've been fiddling around with an Ubuntu, Fedora dual boot the last couple of days and it's definitely an "advanced" undertaking.

 Part of the problem is a :grub2, legacy grub conflict, and then Ubuntu would install a "regular" partition, and Fedora would install something called a LVM partition.

 Anyways, I finally just dual booted to Opensuse/Ubuntu. Those two play together just fine. 

  Good luck...

---

### Post by georgemc on 2010-08-29
Maybe this post can point you in a good direction:

[http://ubuntuforums.org/showthread.php?p=9691590#post9691590](http://ubuntuforums.org/showthread.php?p=9691590#post9691590)

Just recently, within the last 4 weeks or so, I made my laptop to triple boot; XP, U10.04, and F13.  Had to do some trial and error but I did get it to work.

Hope this helps.

George

---

