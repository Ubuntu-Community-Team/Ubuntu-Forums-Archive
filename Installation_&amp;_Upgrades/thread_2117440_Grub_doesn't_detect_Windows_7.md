---
title: "Grub doesn't detect Windows 7"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by cyanide911 on 2013-02-18
I had Win8 installed with Ubuntu running happily. Then I formatted Win8  and installed Win7. Then i repaired Grub. Now Grub doesn't show Windows 7  no matter what I do!

> sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3dd1b453

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   164509695    82050048    7  HPFS/NTFS/exFAT
/dev/sda3       164509696  1221277695   528384000    f  W95 Ext'd (LBA)
/dev/sda4      1221277696  1250050047    14386176    7  HPFS/NTFS/exFAT
/dev/sda5       164511744   244588543    40038400   83  Linux
/dev/sda6       244590592   252837887     4123648   82  Linux swap / Solaris
/dev/sda7       340488192  1221277695   440394752    7  HPFS/NTFS/exFAT
/dev/sda2 is Window 7, /dev/sda5 is my Ubuntu partition.

> sudo os-prober
/dev/sda4:Windows Recovery Environment (loader):Windows:chain
/dev/sda5:Ubuntu 12.04.2 LTS (12.04):Ubuntu:linux
I've tried to update grub as well.

---

### Post by albandy on 2013-02-18
Try with boot repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

