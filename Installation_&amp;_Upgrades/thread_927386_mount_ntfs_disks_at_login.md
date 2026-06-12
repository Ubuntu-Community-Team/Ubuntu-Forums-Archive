---
title: "mount ntfs disks at login"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by rvs070 on 2008-09-22
I just put together a dual boot machine with the ubuntu hd as primary IDE master, WinXP hd as primary IDE slave, and a data disk with two NTFS partitions on SATA channel 0. Here is the output of 'sudo fdisk -lu':

```
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1eb91eb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   136713149    68356543+  83  Linux
/dev/sda2       136713150   156360644     9823747+   5  Extended
/dev/sda5       136713213   148424534     5855661   82  Linux swap / Solaris
/dev/sda6       148424598   156360644     3968023+   b  W95 FAT32

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x765ea672

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    39070079    19535008+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9665ab6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sdc2        81915435   398283479   158184022+   f  W95 Ext'd (LBA)
/dev/sdc5        81915498   398283479   158183991    7  HPFS/NTFS
```

I would like to mount the two partitions on sdc (even though for some reason they are showing up as three partitions in the output above) at login for every user. In other words, I would like to set this up globally. Here are the mount options when I mount the partitions from "Places" in the Gnome toolbar (same for both partitions):

```
rw nosuid nodev noatime relatime user_id=0 goup_id=0 allow_other
```

Oh, and can anyone explain why all three drives got labeled 'sd', even though only one is SATA and the other two are IDE?

---

### Post by rvs070 on 2008-09-23
The other thing I'd like to do is to make these disks available to a Windows network over samba. Or should I not be using samba, since the disks are NTFS to start out with?

And I'd also like to make the printer attached to the dual boot available to both a Windows machine and an eee pc (Xandros) over the network.

I'll appreciate any suggestions!

---

