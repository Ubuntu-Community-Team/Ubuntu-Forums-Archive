---
title: "How do I add a Windows option in GRUB?"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by Stryfe on 2005-05-09
yes I'm a n00b.  I've read tutorials but I can't seem to get it to work.  Here is my info:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            2485        2550      530145   82  Linux swap / Solaris
/dev/hda2               1        2484    19952698+  83  Linux
/dev/hda3   *        2551        9729    57665286    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        8857    71143821    7  HPFS/NTFS
/dev/hdb2   *        8858       14593    46074420    c  W95 FAT32 (LBA)


So, my XP is on: /dev/hda3   *        2551        9729    57665286    7  HPFS/NTFS
After reading tutorials I put this in:

title		Windows XP Professional
root		(hd0,2)
makeactive
chainloader	+1


Is this correct?  It didn't work for me.  It said something like unknown fileslystem or something like that.  What am I doing wrong?  Thanks!

---

### Post by defkewl on 2005-05-09
Yup it has got to do with your filesystem. You're using NTFS. Find some resources on google how grub could detect your NTFS, otherwise use FAT32.
 
:)

---

### Post by kosmic on 2005-05-09
It should be

title Windows
        root (hd1,0)
        makeactive
        chainloader +1 
root (hd1,0) windows is on the partition /dev/hdb and not in /dev/hda (hd0,2)

---

