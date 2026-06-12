---
title: "/boot location"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by opticyclic on 2010-09-01
I am going to reinstall with LVM, LUKS encryption and a /boot partition.
Does it matter where the /boot partition is?

My thoughts are to leave the 2 primary Windows partitions and encrypt them with TrueCrypt and do all the linux stuff in the extended partition (see below).

Would that work? 
Does /boot have to be a primary partition?
Should /boot be the first partition on the disk?
Would it matter if /boot was an unencrypted logical partition in the middle of the disk in the Extended partition?

Currently my setup looks like this:

```
root@PartedMagic:~# parted /dev/sda print

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  53.7GB  53.7GB  primary   ntfs            boot
 2      53.7GB  107GB   53.7GB  primary   ntfs
 3      107GB   160GB   52.7GB  extended                  lba
 5      107GB   146GB   38.7GB  logical   ext4
 6      146GB   151GB   5369MB  logical   ext4
 7      151GB   158GB   6107MB  logical   ext4
 8      158GB   160GB   2147MB  logical   linux-swap(v1)

```

```
root@PartedMagic:~# sfdisk -l

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   6526    6527-  52428096    7  HPFS/NTFS
/dev/sda2       6527   13053-   6527-  52428120+   7  HPFS/NTFS
/dev/sda3      13054+  19457-   6404-  51433730    f  W95 Ext'd (LBA)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      13054+  17759-   4706-  37800848   83  Linux
/dev/sda6      17760+  18412-    653-   5242880   83  Linux
/dev/sda7      18413+  19155-    743-   5963776   83  Linux
/dev/sda8      19196+  19457-    262-   2097152   82  Linux swap / Solaris

```

---

### Post by andrewthomas on 2010-09-01
Does /boot have to be a primary partition? **no**
Should /boot be the first partition on the disk? **no**
Would it matter if /boot was an unencrypted logical partition in the middle of the disk in the Extended partition? **no**

---

### Post by opticyclic on 2010-09-01
Cool. Thanks for the quick reply.
I'll create a 100MB /boot partition in the extended partition then see how difficult the LVM and LUKS is to setup.

---

