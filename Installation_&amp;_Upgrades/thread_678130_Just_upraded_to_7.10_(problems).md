---
title: "Just upraded to 7.10 (problems)"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by kliljedahl on 2008-01-25
Just reinstalled XP & 6.06 Wednesday  to go back to dual boot. Upgraded to 7.04 yesterday & found Automatix was for 7.10 so upgraded to 7.10 this morning. First problem is when I boot up I get all kinds of error messages. Finally reach the point where "control D" will allow me to log on. Now that I have there are issues with recognition of hard drives (I have 4) The 4th is not seen at all. 
 Under "places" there are two discs labeled "disc1", Identical, one labeled "disc 2" which is my second internal. "Disc 3" seems to to be the MS operating system, and one just labeled "Disc" which is my first external.

 I ran sudo fdisk -l and got:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4081    32780601    7  HPFS/NTFS
/dev/sda2            9138        9729     4755240    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3            4082        9137    40612320   83  Linux
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris
/dev/sda6            9138        9355     1751022   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffa8ffa8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdc: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3c9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        5005    40202631   83  Linux

Disk /dev/sdd: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06eb1ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       14946   120053713+  83  Linux
kliljedahl@kliljedahl-desktop:~$ 

The one labeled sdd is the second external? That's the one I see nowhere else.

Also, videos no longer play in Firefox

---

