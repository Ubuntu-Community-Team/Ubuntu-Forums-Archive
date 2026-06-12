---
title: "Problem after upgrade"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by satimis on 2014-09-30
Hi all,

problem after upgrade to 14.04 (from 12.04)

The device for storage and VMs seems invisible.


host	Ubuntu 14.04 (after upgrade)
Oracle VirtualBox

HDD on this box```

Maxtor 160G (another disk for Windows7)
SSD 120G (another disk with Debian running)

```

Starting Virtualbox manager, the VMs are still there and can be started.


$ sudo fdisk -l```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe63b9e7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   312578047   156185600    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008fea2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758   250068991   124783617    5  Extended
/dev/sdb5          501760   250068991   124783616   8e  Linux LVM

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bf74f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      499711      248832   8e  Linux LVM
/dev/sdc2          501758  2930276351  1464887297    5  Extended
/dev/sdc5          501760  2930276351  1464887296   8e  Linux LVM

Disk /dev/mapper/LVM1.5D-root: 300.0 GB, 299997593600 bytes
255 heads, 63 sectors/track, 36472 cylinders, total 585932800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/LVM1.5D-root doesn't contain a valid partition table

Disk /dev/mapper/LVM1.5D-swap: 4999 MB, 4999610368 bytes
255 heads, 63 sectors/track, 607 cylinders, total 9764864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/LVM1.5D-swap doesn't contain a valid partition table

Disk /dev/mapper/LVM1.5D-data: 1195.0 GB, 1195045289984 bytes
255 heads, 63 sectors/track, 145289 cylinders, total 2334072832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/LVM1.5D-data doesn't contain a valid partition table

Disk /dev/mapper/debian731-root: 122.6 GB, 122553368576 bytes
255 heads, 63 sectors/track, 14899 cylinders, total 239362048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/debian731-root doesn't contain a valid partition table

Disk /dev/mapper/debian731-swap_1: 5221 MB, 5221908480 bytes
255 heads, 63 sectors/track, 634 cylinders, total 10199040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/debian731-swap_1 doesn't contain a valid partition table

```


Please advise how to recover/mount the invisible device?  Thanks

Regards
satimis

---

### Post by Maverick Meerkat on 2014-09-30
Hello Satimis,

Sorry I can't help with your question, but your thread is marked "Solved" and I'm sure that might keep some folks from reading it that could help you.
You should be able to Edit your post and change it.

Good luck with your post :-)

Rick

---

### Post by satimis on 2014-09-30
Hi Maverick Meerkat,

Sorry I made a mistake.  VMs and other files are under /data/ folder.  I found on Virtualbox Manager -> Preference later.

satimis

---

