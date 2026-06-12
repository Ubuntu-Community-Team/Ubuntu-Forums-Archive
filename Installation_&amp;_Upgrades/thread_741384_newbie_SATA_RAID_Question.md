---
title: "newbie SATA RAID Question"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by lubovip on 2008-03-31
I'm installing Ubuntu 6.06 LTS.I have following setup:
---PATA Drive 30 GB for OS
---SATA Drive 300GB as part of Software  RAID(2 partitions first-160GB and second -the rest)
---SATA Drive 160GB as part of Software RAID(1 part-160GB)
The reason I'm doing this is I want to setup a fileserver on workgroup(SAMBA with SWAT)
How can I format and mount my RAID ?

when I run  sudo fdisk -l
this is what the console shows


Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3497    28089621   83  Linux
/dev/hda2            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19929   160079661   83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661   83  Linux

Disk /dev/md0: 163.9 GB, 163921461248 bytes
2 heads, 4 sectors/track, 40019888 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table
lubo@ubuntu-server:~$

---

