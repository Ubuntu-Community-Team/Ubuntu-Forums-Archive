---
title: "bad format"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by dracule on 2006-09-13
I just tried to install ubuntu and it made my xp partition bad. Is there any way for me to recover my files?

---

### Post by dracule on 2006-09-13
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        8938    71746290   82  Linux swap / Solaris
/dev/sda3            8940        9545     4867695   db  CP/M / CTOS / ...
/dev/sda4            8939        8939        8032+   5  Extended
/dev/sda5            8939        8939        8001   83  Linux
/dev/sda6            8939        8939          30+  83  Linux

Partition table entries are not in disk order


that is what I got when i did sudo fdisk -l

---

