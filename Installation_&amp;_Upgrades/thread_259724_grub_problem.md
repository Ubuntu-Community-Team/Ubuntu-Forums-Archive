---
title: "grub problem?"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by tempo500 on 2006-09-17
hi,

i am not able to start windows through grub. there are 4 hd's.
hda 160gb ubuntu edgy
hdb 80gb windows

2 serial ata drives

when i want to boot into windows, the computer freezes with a blank screen. i read through most of the forum threads and tried plenty configurations for the menu.lst file... please help me with this, i dont want to change the master in the bios all the time! THANX! phil

```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    30716279    15358108+  83  Linux
/dev/hda2   *    30716280    38909429     4096575   82  Linux swap / Solaris
/dev/hda3        38909430   312576704   136833637+  83  Linux

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    20482874    10241406    7  HPFS/NTFS
/dev/hdb2        20482875   156344579    67930852+   f  W95 Ext'd (LBA)
/dev/hdb5        20482938   156344579    67930821    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   156296384    78148161   fd  Linux raid autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sdb doesn't contain a valid partition table

```

```

title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map 		(hd0) (hd1)
map 		(hd1) (hd0)
chainloader	+1

```

---

### Post by tempo500 on 2006-09-26
are the serial ata's the problem?

---

