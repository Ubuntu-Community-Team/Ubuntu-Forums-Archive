---
title: "Accidentally erased partitions from external USB drive"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by kah-el on 2008-07-27
Hi,

Just installed Ubuntu Studio from CD to internal harddrive, dual-boot with WinXP. Everything fine, except that during installation I failed to notice that my external USB drive was connected, and accidentally first removed the partitions (I think there was only one) and I guess also the MBR too from the drive ("Are you absolutely sure...", "Of course I'm sure...") :oops:.

The external drive is Seagate Free Agent, and I don't think it needs to be bootable (I just use it for data storage), but just now my system (either XP or Ubuntu) cannot read any data from it.

Before any experiments of my own with fdisk, I'd like to get some hints for how to best solve the situation.

> sudo fdisk -l outputs following info:
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a6a67de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4256    34186288+   7  HPFS/NTFS
/dev/sda2            4257       19929   125893372+   5  Extended
/dev/sda5            4257       19741   124383231   83  Linux
/dev/sda6           19742       19929     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
```

Help greatly appreciated.

--
Mikael

---

### Post by Pumalite on 2008-07-27
Get Gparted Live CD and see if you can recover your external drive:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

