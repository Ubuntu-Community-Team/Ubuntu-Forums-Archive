---
title: "file system has an incompatible feature enabled"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by kellemes on 2007-10-20
Ubuntu 7.10 installer gives me this message before partitioning:
```
file system has an incompatible feature enabled
```
After partitioning the messsage is:
```
The test of the file system with type ext2 in partition #1 of SCSI4 (0,0,0) (sdc) found uncorrected errors.
If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.
```

I can continue the procedure but after rebooting the system it hangs at filesystem-check of this partition.

fdisk -l gives:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe6e48204

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdb5               2       24321   195350368+   b  W95 FAT32

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb31ab31a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          67      538146   83  Linux
/dev/sdc2              68        8465    67456935    5  Extended
/dev/sdc5              68         193     1012063+  82  Linux swap / Solaris
/dev/sdc6             194         718     4217031   83  Linux
/dev/sdc7             719        2023    10482379+  83  Linux
/dev/sdc8            2024        4592    20635459+  83  Linux
```


sdc includes another GNU/Linux install I need to keep, the partition Ubuntu has a problem with is sdc1, it's formated ext2 and used as /boot for my other GNU/Linux install. This I don't want to change.

e2fsck/fsck does not report any problems on any of my partitions!

It seems to be bug: [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/37137]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/37137")

Anyone?

---

### Post by kellemes on 2007-10-20
Tried using the alternate installer..
Same problem.

---

### Post by kellemes on 2007-10-20
Well, in order to get Gutsy going I chose to convert ext2 to ext3.. this obviously worked.
Still it sucks the good old ext2 doesn't seem to be supported by Ubuntu, at least not here.
Thumbs down.:x

---

