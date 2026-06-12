---
title: "pendrive problem with vfat partition"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by metaphorz on 2008-01-23
I tried the instructions for creating a live ubuntu 7.10 distribution
on a usb pendrive:

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I am having a problem on step 15 when trying to execute "syslinux". The
problem is that partition 1 is invalid for syslinux's purposes:

root@ubuntu:/mnt# mkfs.vfat -F 16 -n ubuntu710 /dev/sdb1
mkfs.vfat 2.11 (12 Mar 2005)
WARNING: Not enough clusters for a 16 bit FAT! The filesystem will be
misinterpreted as having a 12 bit FAT without mount option "fat=16".
mkfs.vfat: Attempting to create a too large file system
root@ubuntu:/mnt# fdisk /dev/sdb1


I've searched for this error online, but have not seen any answers. Some
suggested trying a fat32 system (step 9), but syslinux doesn't appear to recognize
that as valid.

---

### Post by metaphorz on 2008-01-23
A solution, but also a followup question:

(1) Solution: I was, by mistake, entering fdisk /dev/sdb1 instead
     of fdisk /dev/sdb at step 7

(2) Problem: This procedure, while it creates a very nice pendrive
for Linux, doesn't allow me to use the full extent of the remainder
of the drive (an 8GB drive) for Windows Vista/XP. I tried 
replacing steps 11 with mkfs.vfat -F 32 and changed the type
of partition 2 to FAT32 ... to format partition #2,
and while this works, when I plug the USB key while running
Windows, I can see only the first partition, not the second. It
would seem that Windows doesn't allow one to see anything
other than the first partition?

---

