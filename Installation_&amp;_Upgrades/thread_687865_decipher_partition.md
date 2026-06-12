---
title: "decipher partition"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by n2stc on 2008-02-04
I think I may have left part of my first hard drive unformatted/unmounted.  I thought I may want to use it for XP later.  Did I?  Is there a way to recover it safely?

 Here is the output from sudo fdisk -l
> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ce17ce1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        4865    19543072+   5  Extended
/dev/sda5            2433        2554      979933+  82  Linux swap / Solaris
/dev/sda6            2555        4865    18563076   83  Linux

Disk /dev/sdb: 4321 MB, 4321787904 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe406e406

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         261     2096451    b  W95 FAT32
/dev/sdb2             262         524     2112547+   5  Extended
/dev/sdb5             262         524     2112516    b  W95 FAT32
  

Thanks in advance,
Stan

---

### Post by Pumalite on 2008-02-04
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk, boot from it and find out.
(post screenshot)

---

### Post by n2stc on 2008-02-04
Here it is  (I hope)

---

### Post by Pumalite on 2008-02-05
If this is sda and you only have Ubuntu there it looks strange. There is no unallocated space in your first drive.

---

### Post by n2stc on 2008-02-11
I can't create directories in one of the 17 gig spaces.  Strange how?

---

### Post by Pumalite on 2008-02-11
You have one 18.63, another 18.64 and a third 17.70. Which one are you referring to?
Post:
sudo fdisk -lu
mount
cat /etc/fstab

---

