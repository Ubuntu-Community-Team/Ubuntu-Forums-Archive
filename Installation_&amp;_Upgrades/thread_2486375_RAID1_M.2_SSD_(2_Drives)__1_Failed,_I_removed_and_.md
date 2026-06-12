---
title: "RAID1 M.2 SSD (2 Drives) | 1 Failed, I removed and Replaced with a new one, but its s"
date: 2023-04-27
forum: Installation &amp; Upgrades
---

### Post by tj0xin on 2023-04-27
[COLOR=#232629][FONT=-apple-system]I have a Ubuntu Server RAID1 M.2 SSD (2 Drives) where 1 Failed, I removed and Replaced with a new one, but its state stays "removed".[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I am new to RAID Stuff, Below are my RAID Details:[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]**cat /proc/mdstat**[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] md0 : active raid1 nvme1n1p2[0] 1952279552 blocks super 1.2 [2/1] [U_] bitmap: 9/15 pages [36KB], 65536KB chunk[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]unused devices:[/FONT][/COLOR]
[HR][/HR][COLOR=#232629][FONT=-apple-system]**sudo mdadm -D /dev/md0**[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]/dev/md0: Version : 1.2 Creation Time : Tue Apr 25 09:09:58 2023 Raid Level : raid1 Array Size : 1952279552 (1861.84 GiB 1999.13 GB) Used Dev Size : 1952279552 (1861.84 GiB 1999.13 GB) Raid Devices : 2 Total Devices : 1 Persistence : Superblock is persistent[/FONT][/COLOR]
 Intent Bitmap : Internal

   Update Time : Thu Apr 27 07:21:56 2023
         State : active, degraded
Active Devices : 1
[COLOR=#232629][FONT=-apple-system]Working Devices : 1 Failed Devices : 0 Spare Devices : 0[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Consistency Policy : bitmap[/FONT][/COLOR]
          Name : ubuntu-server:0
          UUID : a3f233d6:b8695ca1:f765d639:f03347fa
        Events : 2541

Number   Major   Minor   RaidDevice State
   0     259        3        0      active sync   /dev/nvme1n1p2
   -       0        0        1      removed


Someone please guide

---

### Post by MAFoElffen on 2023-04-27
Easy... Follow this guide: [https://www.thegeekdiary.com/replacing-a-failed-mirror-disk-in-a-software-raid-array-mdadm/](https://www.thegeekdiary.com/replacing-a-failed-mirror-disk-in-a-software-raid-array-mdadm/)

---

