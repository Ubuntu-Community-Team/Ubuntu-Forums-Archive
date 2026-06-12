---
title: "USB HDD wierdness but pen drive is fine?"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by flip2892 on 2008-10-31
Hi, I've been running 8.10 (beta) off of an 8gb USB stick for a couple of weeks now (with very few issues...fewer than with windows) Missus will not let me strip windows so I decided to install to a 40gb usb drive so as to have better speed and more head room. Installed as per my usb stick install but it will not boot. It just says no bootable sector, which I can't work out as I removed all other drives (usb pen drive and internal HDD) when I installed to ensure boot sector would be on the usb hdd.
If I boot via usb stick then the usb hdd is there and can be opened etc???
What is going wrong? Any ideas greatfully recieved.
Thanks in advance.
flipper

---

### Post by flip2892 on 2008-10-31
Don't know if this helps anyone to ttell me what's wrong? I'm begining to think it's a hardware/bios issue????
flipper


flipper@flipper-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2   *      160650   149998904    74919127+   7  HPFS/NTFS
/dev/sda3       149998905   156296384     3148740   db  CP/M / CTOS / ...

Disk /dev/sdb: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4114400b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    14892254     7446096   83  Linux
/dev/sdb2        14892255    15647309      377527+   5  Extended
/dev/sdb5        14892318    15647309      377496   82  Linux swap / Solaris

Disk /dev/sdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe127e2b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    74846834    37423386   83  Linux
/dev/sdc2        74846835    78140159     1646662+   5  Extended
/dev/sdc5        74846898    78140159     1646631   82  Linux swap / Solaris
flipper@flipper-laptop:~$

---

