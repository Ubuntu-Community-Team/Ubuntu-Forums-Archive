---
title: "Fixing Grub to Load Windows"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by kaspien on 2010-01-04
My system previously had Windows 7, which had some issues so I installed Windows XP on a second drive and used that instead.

Yesterday I replaced Windows 7 with Ubuntu 9.10 and invariably wiped out the boot loader. 

Grub lists my XP partition but Windows throws an error when I try to load it, complaining of missing files.

Here's the setup:

[LIST]
[*]Ubuntu 9.10
[*]Windows XP
[*]Media drive
[*]Backup drive
[/LIST]
Here's my fdisk -l:

> root: fdisk -l

Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93929392

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8665    69601581   83  Linux
/dev/sda2            8666        9039     3004155    5  Extended
/dev/sda5            8666        9039     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3980569

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9040    72610816    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e7d9157

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3b6f901

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976759808    7  HPFS/NTFS


What can I do to get Windows XP to load appropriately?

---

### Post by Mark Phelps on 2010-01-04
GRUB can't load windows.  All it can do is hand over control to the Windows boot loader.  In the case of XP, this is the NTLDR file.

So, to be able to boot back into XP, you will have to obtain an XP CD and copy all the boot loader files onto your Windows partition.

---

### Post by kaspien on 2010-01-04
> **Mark Phelps said:**
> So, to be able to boot back into XP, you will have to obtain an XP CD and copy all the boot loader files onto your Windows partition.

What's the proper way of doing it?

Will I need to repair the Windows boot loader, or is it possible to copy the  files?

---

### Post by drs305 on 2010-01-04
This should give you what you need:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

