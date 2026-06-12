---
title: "REinstall or Delete Ubuntu partition"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by vvtelc on 2008-08-05
I need to reinstall or delete by ubuntu partition without afffecting my windows patition, i am afraid to delete the partition because i am not sure that it is the right one. Shouldnt there be a easy way to reinstall ubuntu?

---

### Post by tuxerman on 2008-08-05
Try the command **sudo fdisk -l**. On my system it says:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a00f531

 Device Boot        Start         End      Blocks   Id  System
/dev/sda1   *           1        1151     9245376    7  HPFS/NTFS
/dev/sda2            1152        2307     9285570   83  Linux
/dev/sda3            2308        2433     1012095   82  Linux swap / Solaris
/dev/sda4            2434        9729    58605120    f  W95 Ext'd (LBA)
/dev/sda5            2434        4866    19543041    b  W95 FAT32
/dev/sda6            4867        7299    19543041    b  W95 FAT32
/dev/sda7            7300        9729    19518943+   b  W95 FAT32

```

Of course, yours may be different. Pay attention to the first and last column. The one that corresponds to System: Linux (/dev/sda2 in mine) is the one on which your linux OS is installed. Use your custom-partitioning tool carefully during reinstall - erase this partition and install ubuntu again on it.

---

