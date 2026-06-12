---
title: "External USB drive won't mount"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Ryan8720 on 2007-04-20
After upgrading to Feisty my 80 GB external hard drive stopped working.  The drive was still shown on the desktop, but couldn't be accessed.  So I ejected it. When I unplug and then plug it back in it says it can't mount the drive.

The output from "sudo fdisk -l" shows this:
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4775    38355156   83  Linux
/dev/sda2            4776        4865      722925    5  Extended
/dev/sda5            4776        4865      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   c  W95 FAT32 (LBA)
```

---

