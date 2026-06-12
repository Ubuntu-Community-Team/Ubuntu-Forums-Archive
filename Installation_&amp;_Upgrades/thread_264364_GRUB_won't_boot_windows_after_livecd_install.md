---
title: "GRUB won't boot windows after livecd install"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by mx6string on 2006-09-24
So I had Windows xp installed for quite a while and decided to install ubuntu so i could dual boot, because i prefer to use ubuntu for things like using django and mysql and things like that.  

During the install from the livecd I selected for the installer to resize the current partition (186GB) and use freed space.  I defragmented and got all of the files to the front of the drive before i began all of this partitioning btw.  so anyway I resized to give about 16GB to ubuntu and when i restarted ubuntu boots fine, but when I try to boot "windows XP home edition" from GRUB I just see the echoed code:

root (hd0,0)
   Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

then i'm just left with a blinking cursor at the bottom of this and nothing happens, even if i leave it for a while.  All i can do it Ctrl+Alt+Del to restart and boot into Ubuntu.

I can go to administration > Disks and still see my "Windows NTFS" partition, and it looks like all the files are still there just cant boot

---

### Post by Irony on 2006-09-24
What does;

[PHP]sudo fdisk -l[/PHP]

give you.

---

### Post by mx6string on 2006-09-24
sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22111   177606576    7  HPFS/NTFS
/dev/sda2           22112       24227    16996770   83  Linux
/dev/sda3           24228       24321      755055    5  Extended
/dev/sda5           24228       24321      755023+  82  Linux swap / Solaris

---

