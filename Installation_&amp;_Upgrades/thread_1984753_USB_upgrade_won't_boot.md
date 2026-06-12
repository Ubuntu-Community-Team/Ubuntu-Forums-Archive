---
title: "USB upgrade won't boot"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by hollywoodpete on 2012-05-22
I used the upgrade box in update manager to go from 11.10 to 12.04. I had too many problems so I tried to do a clean install from a USB drive. I can't get the computer to boot without the drive in place. I saw other people had similar problems but not close enough for me to figure out.


I still havent been able to get Ubuntu 12.04 installed on my computer after 2 days.  I get Live to work fine but when I click install I get a spinning CD curser but no instalation. I have tried 2 different harddrives but still no success. Any help would be appreciated. I can run terminal from live with no problem

---

### Post by hollywoodpete on 2012-05-24
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1b79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   153694207    76846080   83  Linux
/dev/sda2       153696254   156248063     1275905    5  Extended
/dev/sda5       153696256   156248063     1275904   82  Linux swap / Solaris

Disk /dev/sdb: 3879 MB, 3879731200 bytes
120 heads, 62 sectors/track, 1018 cylinders, total 7577600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005c4bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7573919     3786929    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

