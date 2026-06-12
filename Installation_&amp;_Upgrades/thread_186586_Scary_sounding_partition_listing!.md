---
title: "Scary sounding partition listing!"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by ngch on 2006-06-02
I did a fresh install of Drapper to dual-boot with winxp pro. During installation, i let the installer do the partitioning for me using the continous free space I've created on my hard disk. After installing, I ran the [COLOR="Red"]fdisk -l[/COLOR] command and this is what I get:


Disk /dev/hda: 41.1 GB, 41110142976 bytes
16 heads, 63 sectors/track, 79656 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       20321    10241406    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           40641       79656    19663560    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3   *       20321       39733     9783585   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           39733       40641      457852+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5           39733       40641      457821   82  Linux swap / Solaris

Partition table entries are not in disk order


Is this a cause for alarm?

---

