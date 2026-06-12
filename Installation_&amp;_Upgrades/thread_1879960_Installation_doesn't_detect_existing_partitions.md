---
title: "Installation doesn't detect existing partitions"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by retrac1324 on 2011-11-12
I am trying to install Ubuntu 11.10 in a dual boot with my existing Windows 7 but the installer does not detect any existing partitions and GParted shows no partitions, only unallocated space.

I have tried resetting my BCD using EasyBCD and doing fixmbr from the Windows startup disc. I while ago I had to use TestDisk to recover my partition table so this might be the cause.

---

### Post by darkod on 2011-11-12
If the disk was ever used in raid have you tried removing the raid meta data because it doesn't get removed by formatting?

From live mode:
sudo dmraid -E -r /dev/sda

If you suspect your disk has something funny, from live mode try:

sudo fdisk -l

or open Gparted and take a look at the partitions.

Do you use Dynamic disk in windows maybe?

---

### Post by retrac1324 on 2011-11-12
> **darkod said:**
> If the disk was ever used in raid have you tried removing the raid meta data because it doesn't get removed by formatting?

From live mode:
sudo dmraid -E -r /dev/sda

If you suspect your disk has something funny, from live mode try:

sudo fdisk -l

or open Gparted and take a look at the partitions.

Do you use Dynamic disk in windows maybe?

I have never used the drive in RAID.

In Disk Management and Acronis Disk Director in Windows, it shows the single Windows 7 partition only, as expected.

I don't think I'm using a Dynamic disk though I don't know how to check.

GParted doesn't see any partitions and only unallocated space.

---

### Post by darkod on 2011-11-12
In windows disk management, where the graphical image is (not the list of partitions above), it will say to the left something like:
Disk 0
Basic

or
Disk 0
Dynamic

Very strange if Gparted also sees it as unallocated. Something is definitely wrong. Usually Gparted is great for disk management.

---

### Post by retrac1324 on 2011-11-12
> **darkod said:**
> In windows disk management, where the graphical image is (not the list of partitions above), it will say to the left something like:
Disk 0
Basic

or
Disk 0
Dynamic

Very strange if Gparted also sees it as unallocated. Something is definitely wrong. Usually Gparted is great for disk management.

Disk Management shows the drive is basic. GParted still shows 100% unallocated space. The drive itself is fine physically, I haven't had problems with it and have installed Ubuntu, Windows, etc on it many times. I think it's a problem with the partition table since I had it recovered using TestDisk.

fdisk -l output:

> Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x360555e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1250274689   625136321    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 7803 MB, 7803174912 bytes
255 heads, 63 sectors/track, 948 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f795a8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          63    15240575     7620256+   c  W95 FAT32 (LBA)



---

### Post by darkod on 2011-11-13
Well, the point of testdisk is that once you fix the problem and are happy with it, it writes the new partitions table to the disk. So in future the disk should look "normal" to all software.

Maybe going into testdisk again and rewriting the partition table might help. But I don't know if that's any danger for the current data.

---

