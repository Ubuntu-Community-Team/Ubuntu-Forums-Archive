---
title: "Instalation over old linux"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by Tetrohedron on 2012-07-25
Does the ubuntu installer have a tool to automatically write Ubuntu over older versions of linux or ubuntu?  If not, how do I ensure that the old linux is removed correctly, and that the new version is installed correctly?

---

### Post by arpanaut on 2012-07-25
Yes, the installer has this ability, but not automatic.

Do you have a single boot, dual boot?
To help us with more information, open a terminal and post here the result of:
```
sudo fdisk -lu
```

---

### Post by Tetrohedron on 2012-07-25
I am dual booting ubuntu and Windows 7.  Here is what the terminal returned when I gave it that command.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b432b97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1258432511   629112832    7  HPFS/NTFS/exFAT
/dev/sda3      1929521152  1953122303    11800576    7  HPFS/NTFS/exFAT
/dev/sda4      1258434558  1929521151   335543297    5  Extended
/dev/sda5      1258434560  1912760319   327162880   83  Linux
/dev/sda6      1912762368  1929521151     8379392   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 8580 MB, 8580497408 bytes
255 heads, 63 sectors/track, 1043 cylinders, total 16758784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb893eaf

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Disk /dev/sdf: 8019 MB, 8019509248 bytes
251 heads, 44 sectors/track, 1418 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2192    15663103     7830456    b  W95 FAT32

---

### Post by oldfred on 2012-07-26
You can use Something Else or manual install. That gives the option to use your existing sda5 as / (root) and choose format (ext4). It should automatically find swap and install.

You can also use gparted from liveCD/USB and delete the Linux partitions and reinstall to the unallocated space.

---

