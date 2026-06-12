---
title: "Messy raid1 disk system"
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by tegelstom on 2014-09-07
Here is my messy raid1 server's disk system situation:
[https://plus.google.com/u/0/photos/112478144887851328209/albums/5736976833890696177/6056271231707137714?pid=6056271231707137714&oid=112478144887851328209](https://plus.google.com/u/0/photos/112478144887851328209/albums/5736976833890696177/6056271231707137714?pid=6056271231707137714&oid=112478144887851328209)
-disk 0 (WINDOWS C) is made from two(2) physical disks /dev/sda and /dev/sdb and holds the Windows 2003 system and I guess is the boot point.
-disk 1, another physical disk, partitioned in four(4) partitions:
  a) /dev/sdc1, WIN_DATA D:, that holds users data 
  b) /dev/sdc2, /(root), gonna mount the Ubuntu root filesystem
  c) /dev/sdc3, /home, gonna mount the Ubuntu /home filesystem for users data.
  d) /dev/sdc4 the swap partition
-disk 2, G,  an external usb backup disk.
I 've tried to install Ubuntu 14.04 grub in two ways:
First I installed the grub on /dev/mapper...something device that appears during Ubuntu installation.
Second I installed the grub on /dev/sda device.
In both cases only Ubuntu shows up after installation and cannot have a dual boot system Windows 2003/Ubuntu 14.04.
Any help here please?
Btw, I got so frustrated that I'm thinking to remove the raid1 system by plugging off the /dev/sdb device, but also I need some advice here.
Thanks In Advance
Thomas

---

### Post by tegelstom on 2014-09-11
I had a hardware raid1, I disabled it via BIOS, and now I have a cool dual boot server windows2003/ubuntu14.04 system.

---

