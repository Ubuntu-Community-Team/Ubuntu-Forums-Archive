---
title: "Vista Dual Boot (Disks Separate)"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by budman21901 on 2008-05-04
I have tried everything under the sun to get these to OS's to dual boot with separate drive.  This has truly been a nightmare!  I am not a novice to Linux, but this is killing me!  Maybe i am over looking something obvious.

**Device Map **
[HTML](hd0)	/dev/sda  (Vista)  
(hd1)	/dev/sdb  (Linux)  
(hd2)	/dev/sdc  (Storage)[/HTML]

**Fdisk -L  **
[HTML] Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ffc8ffc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9713    78015488    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e1609

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8694        9726     8297572+  83  Linux
/dev/sdb2            8311        8693     3076447+  82  Linux swap / Solaris
/dev/sdb3               1        8310    66750043+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf07cf07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS[/HTML]


**Notes **

Vista loader is restored on hda. A straight boot goes vista.

Booting with Super Grub CD gets me to Linux.  

The boot loader i need is on the Linux Disk (hdb)  Putting it on hda just gets it wiped by vista. 

Telling my bios to boot hdb does not work.  It wont grab the MBR from it.  I have done this type of thing a thousand times until vista came out.  Now it been nothing but a config nightmare.

I can get to Linux with super grub so its not super critical but it is bugging the crap out of me.  If you have any suggestions let me know, and i will try them!

---

### Post by zvacet on 2008-05-04
You can try [this.]("http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot")

---

