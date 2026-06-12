---
title: "Installation onto an external USB HDD"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by tuxerman on 2010-11-07
I'm dual booting Kubuntu Lucid and Windows XP on my comp. I have a 320 GB external USB hard disk. I installed ubuntu lucid onto it, and chose the option to install grub to /dev/sdb (my 320gig hdd) before commencing install.

However, on booting from the external, I get "unknown filesystem. Grub rescue>" on the screen.

If I'm right, the choosing where to install grub is the only change u gotta make while installing. Any ideal how to get this fixed?

---

### Post by tuxerman on 2010-11-07
Incase anyone wants the output of fdisk -l, here it is :D

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3a00f531

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1151     9245376    7  HPFS/NTFS
/dev/sda2            1152        2307     9285570   83  Linux
/dev/sda3            2308        2433     1012095   82  Linux swap / Solaris
/dev/sda4            2434        9729    58605089+   f  W95 Ext'd (LBA)
/dev/sda5            2434        4867    19543072    b  W95 FAT32
/dev/sda6            4867        7299    19543041    b  W95 FAT32
/dev/sda7            7300        9729    19518943+   b  W95 FAT32

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bf599

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36363   292085766    c  W95 FAT32 (LBA)
/dev/sdb2   *       36364       38792    19508224   83  Linux
/dev/sdb3           38792       38914      974849    5  Extended
/dev/sdb5           38792       38914      974848   82  Linux swap / Solaris

```

---

### Post by tuxerman on 2010-11-07
bump

---

