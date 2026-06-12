---
title: "Update to Kernel 2.6.38-11 fails to boot"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by WildeBeest on 2011-08-23
[LEFT]Natty kernels 2.6.38-8 and -10 boot just fine. 64 bit

Dual boot with Win7 and Natty on separate 250GB drives. There is also a raid 0 drive.

38-11 gives me the following errors.

udevd-work[94]: inotify_add_watch(6, /dev/sdb, 10) failed: No such file or directory

udevd-work[96]: inotify_add_watch(6, /dev/sdd, 10) failed: No such file or directory


The output of fdisk -l

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a3e8b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244093952    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003b7d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7968    63998976   83  Linux
/dev/sdc2            7968        8964     7999489    5  Extended
/dev/sdc5            7968        8964     7999488   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00890089

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00890089

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/dm-1: 80.0 GB, 80031776768 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00890089

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/dm-2: 80.0 GB, 80023716864 bytes
255 heads, 63 sectors/track, 9728 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```


[/LEFT]

---

### Post by WildeBeest on 2011-08-24
Anyone?

---

### Post by WildeBeest on 2011-08-26
No one?

---

### Post by WildeBeest on 2011-08-27
I can't believe no one can help with this issue.

---

### Post by WildeBeest on 2011-09-06
Is there anybody out there?

---

### Post by fig_wright on 2011-09-18
[http://ubuntuforums.org/showthread.php?p=11200815](http://ubuntuforums.org/showthread.php?p=11200815)

---

