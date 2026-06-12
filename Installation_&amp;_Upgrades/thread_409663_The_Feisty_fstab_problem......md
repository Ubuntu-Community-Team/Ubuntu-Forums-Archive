---
title: "The Feisty fstab problem....."
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by OldGaf on 2007-04-14
Hi,

I got a daily build a few days ago and installed it. Tonight I am having the fstab problem were drives are being renamed every time I boot. ie. sda1 becomes sdf1 or sdb1 on every boot.

My question is, if I download todays daily build and reinstall, will I avoid this kernel bug?

---

### Post by OldGaf on 2007-04-15
OK..... I got the latest daily build and installed. After that there was only kernel related updates available. Updated and rebooted. 
fdisk did keep changing on every boot and my fstab had my DVD and CD labeled incorrectly. Once I fixed the optical devices in fstab, everything seems to have settled down.

Disk /dev/sde: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde2               1       14946   120053713+   5  Extended
/dev/sde5           14339       14946     4883728+  82  Linux swap / Solaris
/dev/sde6   *           1       12158    97659040+  83  Linux
/dev/sde7           12159       14338    17510818+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        4866    39078112+   f  W95 Ext'd (LBA)
/dev/hdb5               2        4865    39070048+   b  W95 FAT32

-----------------------------------------------------------------------------------------

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       14946   120053713+   5  Extended
/dev/sda5           14339       14946     4883728+  82  Linux swap / Solaris
/dev/sda6   *           1       12158    97659040+  83  Linux
/dev/sda7           12159       14338    17510818+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        4866    39078112+   f  W95 Ext'd (LBA)
/dev/hdb5               2        4865    39070048+   b  W95 FAT32

---

