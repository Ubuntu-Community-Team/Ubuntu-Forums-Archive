---
title: "&quot;not enough swap&quot; while trying hibernate"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by hmdknight on 2012-07-05
hi
I've got ubuntu 12.04 installed on a 20GB partition via Wubi (install within windows 7). the problem is when I try 'sudo pm-hibernate', the "not enough swap" pops up. ram capacity is 4GB while swap is 256MB. when booting with a live cd and trying 'gparted', the only thing I get is a 20GB ntfs partition. so is there any way to increase the swap in order to enable hibernate?

---

### Post by sudodus on 2012-07-05
Welcome to the Ubuntu Forums :-)

If you post some data about your drives, it will be easier to help. Please post the output of the following command from a terminal window
```
sudo fdisk -lu
```

---

### Post by westie457 on 2012-07-05
Hi, the reason hibernate is not working is in this post. [http://ubuntuforums.org/showpost.php?p=9980326&postcount=5](http://ubuntuforums.org/showpost.php?p=9980326&postcount=5)

How to get it to work is in this thread. [http://ubuntuforums.org/showthread.php?t=1597982](http://ubuntuforums.org/showthread.php?t=1597982)

Good luck

---

### Post by hmdknight on 2012-07-05
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

If you post some data about your drives, it will be easier to help. Please post the output of the following command from a terminal window
```
sudo fdisk -lu
```

thanx
here is is the outpt:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x999802a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   167774207    83783680    7  HPFS/NTFS/exFAT
/dev/sda3       167782860   976769023   404493082    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda5       167782923   209712509    20964793+   7  HPFS/NTFS/exFAT
Partition 5 does not start on physical sector boundary.
/dev/sda6       209717248   587204607   188743680    7  HPFS/NTFS/exFAT
/dev/sda7       587204672   976769023   194782176    7  HPFS/NTFS/exFAT

```

---

### Post by sudodus on 2012-07-05
> **hmdknight said:**
> thanx
here is is the outpt:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x999802a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   167774207    83783680    7  HPFS/NTFS/exFAT
/dev/sda3       167782860   976769023   404493082    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
[COLOR="Red"]/dev/sda5       167782923   209712509    20964793+   7  HPFS/NTFS/exFAT[/COLOR]
Partition 5 does not start on physical sector boundary.
/dev/sda6       209717248   587204607   188743680    7  HPFS/NTFS/exFAT
/dev/sda7       587204672   976769023   194782176    7  HPFS/NTFS/exFAT

```
I guess you have installed Ubuntu into /dev/sda5 because it is 20 GB. But a wubi install means its file system is inside a file instead of directly in a partition. Check that this is really the case, when booted from an Ubuntu install disk 'try without installing'.

Is the system new, or have you created a lot of private files and done a lot of tweaking?

First, ***backup*** your hard drive to an external drive (or at least Windows and your private files, because editing partitions is risky.

If the system is new, I suggest that you make a new install, this time a dual boot install.
- boot your computer from the Ubuntu CD or USB drive.
- when you arrive at the partitioning window, select 'Something else' meaning that you select partitions manually.
- wipe the partition (assuming /dev/sda5)
- make a swap partition of 4.5 GB
- make an ext4 partition of the rest of the unused space (approx 15.5 GB)
- select the swap partition as swap
- select the ext4 partition as root (/)
- install grub to /dev/sda (*not* dev/sda5)
and then I think you can continue

If your system is old we have to discuss more about what is the best option, but make good backup anyway.

---

### Post by hmdknight on 2012-07-07
thnx, solved

---

