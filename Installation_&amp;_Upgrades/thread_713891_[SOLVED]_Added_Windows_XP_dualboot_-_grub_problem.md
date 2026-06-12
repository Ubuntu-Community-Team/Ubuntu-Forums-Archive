---
title: "[SOLVED] Added Windows XP dualboot - grub problem"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by peterthebike on 2008-03-03
I reduced the size of my Ubuntu partition, added a fat32 partition for Windows XP, installed XP, but cannot install grub correctly.

Following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=224351") I tried to find the file stage1 but this happened:
```
grub> find /boot/grub/stage1

Error 15: File not found

grub> 

```
My partitions are:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         269     2104515    b  W95 FAT32
/dev/sda3   *         270         294      200812+  83  Linux
/dev/sda4             295       38913   310207117+   f  W95 Ext'd (LBA)
/dev/sda5             295         456     1301233+  82  Linux swap / Solaris
/dev/sda6             457       37638   298664383+  83  Linux
/dev/sda7           37639       38913    10241406    b  W95 FAT32

```

Can someone offer some help please?

---

### Post by peterthebike on 2008-03-03
I found another thread which explained the hd0,0 values.

As I have one harddisk and the file stage1 is in the third partion, values of hd0,2 for the root and setup commands got me working again.

---

