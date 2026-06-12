---
title: "Problems mounting second internal hard drive."
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by ventnormatt on 2008-10-27
Hello. 

I've recently reinstalled ubuntu 8.04. Originally I had a dual boot with windows and was attempting to repair the windows installation but only succeeded in damaging the boot sector (I think). So, I have now reinstalled ubuntu and windows xp on a spare hard drive and now wish to access all the files on the original hard drive. Using XP I can see the drive but it claims it is unformatted - I guess it just doesn't recognise it, no worries here. However, Ubuntu cannot see it at all. However the output from fdisk shows it, here below:

Disk /dev/sda: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x932e932e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1283    10305666    7  HPFS/NTFS
/dev/sda2            1284        4867    28788480    5  Extended
/dev/sda5            1284        4713    27551443+  83  Linux
/dev/sda6            4714        4867     1236973+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
86 heads, 15 sectors/track, 242311 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sdb1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           1      208090   134217727+   4  FAT16 <32M

sda (40gb) is my boot disk, sdb (160gb) is the storage disk that I can't mount.

Question is how do I get ubuntu to mount the drive so that I can use it, and get my data back. Many thanks indeed!

Matt

---

### Post by logos34 on 2008-10-27
You're best bet is to try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") or PhotoRec.

---

### Post by ventnormatt on 2008-12-03
Thanks for this. I'll give it a go. Sorry for the massive delay in replying. Few problems with the computer after posting then busy elsewhere! 

Cheers again though.

M.

---

