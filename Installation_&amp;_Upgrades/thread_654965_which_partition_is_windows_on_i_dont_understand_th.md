---
title: "which partition is windows on? i dont understand the terminal output"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by templa edhel on 2007-12-31
i am dual bootinf ubuntu and xp media edition but when i partitioned my disk i think boot.ini got messed up. i know how to fix it IF i can figure out what partition windows is on. ```
sudo fdisk -l
``` reads ```
Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2439        8517    48829567+   5  Extended
/dev/sda2   *           7        2438    19535040    7  HPFS/NTFS
/dev/sda3            8518       11131    20996955    7  HPFS/NTFS
/dev/sda4           11372       11977     4867695   db  CP/M / CTOS / ...
/dev/sda5   *        2439        8262    46781248+  83  Linux
/dev/sda6            8263        8517     2048256   82  Linux swap / Solaris

Partition table entries are not in disk order

```
so i want to know what order they are in if they not in disk order. i remember on the partition menu (alternate cd) the partitons started at 2 not 1 for some reason. is it on partition 7?

---

### Post by taurus on 2007-12-31
> **templa edhel said:**
> i am dual bootinf ubuntu and xp media edition but when i partitioned my disk i think boot.ini got messed up. i know how to fix it IF i can figure out what partition windows is on. ```
sudo fdisk -l
``` reads ```
Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2439        8517    48829567+   5  Extended
**[COLOR="Blue"]/dev/sda2   *           7        2438    19535040    7  HPFS/NTFS[/COLOR]**
/dev/sda3            8518       11131    20996955    7  HPFS/NTFS
/dev/sda4           11372       11977     4867695   db  CP/M / CTOS / ...
/dev/sda5   *        2439        8262    46781248+  83  Linux
/dev/sda6            8263        8517     2048256   82  Linux swap / Solaris

Partition table entries are not in disk order

```
so i want to know what order they are in if they not in disk order. i remember on the partition menu (alternate cd) the partitons started at 2 not 1 for some reason. is it on partition 7?

That should be your bootable windows partition.

---

### Post by Irihapeti on 2007-12-31
The partitions are listed in numerical order. i.e. /sda1 to /sda6. By the look of it, your Windows installation is on /dev/sda2, because your /sda2 partition is at the beginning of the disk and is NTFS file format. Best to check this, though, by examining the partition and seeing that it has the usual Windows OS files/folders on it.

Edit: Someone else was quicker off the mark!

---

### Post by logos34 on 2007-12-31
your boot.ini default entry should be pointing to the second partition:
> 
default=multi(0)disk(0)rdisk(0)partition(**2**)\WINDOWS

The 'root' line in your windows entry in /boot/grub/menu.lst should be:
> 
title Windows XP MCE
root (hd0,**1**)
...

---

