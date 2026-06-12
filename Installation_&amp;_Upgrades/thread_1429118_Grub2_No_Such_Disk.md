---
title: "Grub2 No Such Disk"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by uRock on 2010-03-13
I have a Dell machine with two hard drives that has Windows XP Home on the first disk (sda) and I just installed Karmic to the second hard disk(sdb) and when the install finished installing Grub2 to the MBR and the system restarted, I get the no such disk error and the grub rescue prompt. There is no option in BIOS to boot from the second disk.

What do I need to do to get this working?

Thanx,
Ronnie

---

### Post by uRock on 2010-03-13
Here is the output of fdisk -l via the LiveCD
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        9725    78083932+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd135d135

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1284    10313698+  83  Linux
/dev/sdb2            1551       14593   104767897+   5  Extended
/dev/sdb3            1285        1550     2136645   82  Linux swap / Solaris
/dev/sdb5            8203       14593    51335707+   7  HPFS/NTFS
/dev/sdb6            1551        8202    53432127   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```

---

### Post by uRock on 2010-03-13
Ok, I used Lilo to repair the MBR and remove grub. Now to swap the master/slave and let grub be where it can work right.

---

