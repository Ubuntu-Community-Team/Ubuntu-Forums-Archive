---
title: "Partitioner not detecting partition table"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by Kazagistar on 2011-02-03
I am trying to install Ubuntu over a previous install, parallel with my Truecrypted windows partition, but the installer does not detect a partition table on the hard drive. However, the drop down menus "Places" sees the Linux drives, and I can browse through the files; only the installer is blind to it's existence.

---

### Post by oldfred on 2011-02-03
I do not know if the Truecrypt is confusing things, but it may be just that you have used all 4 primary partitions?

Does Truecrypt tell you how to partition a drive if one partition is encrypted?

I have this in my notes from a long time ago so I do not know if it is still current:
Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.

---

### Post by psusi on 2011-02-03
This is usually due to minor corruption of the partition table.  Post the output of sudo fdisk -lu.

---

### Post by Kazagistar on 2011-02-03
```
ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda
omitting empty partition (5)

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9fca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   781240949   390620443+   7  HPFS/NTFS
/dev/sda2       781252606  1250263039   234505217    5  Extended
/dev/sda3      1219014656  1250263039    15624192   82  Linux swap / Solaris
/dev/sda5       781252608   791015423     4881408   83  Linux
/dev/sda6       791017472  1219010559   213996544   83  Linux
```

So yeah, it looks fine to me, but the installer does not detect the partition table existing at all.

---

### Post by psusi on 2011-02-03
It is corrupt: sda2 overlaps sda3.  Since it is a swap partition you should be ok if you just delete it.  What sort of partition operations have you done lately on the drive with what tools?  It would be handy to identify what broken program caused this.

---

### Post by Kazagistar on 2011-02-04
Actually, all the partitions other then sda1 are expendable, so I deleted them all in fdisk, and it worked, thanks for the tip. As to what apps were used to edit it, the Ubuntu Disk Management tool created it, and possibly the Truecrypt bootloader installer edited it.

---

