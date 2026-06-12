---
title: "eah... mounting software raid"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by tempo500 on 2006-09-29
i am stuck somewhere between formating and mounting my 2 software raid hds...

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   312592769   156296353+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   156296384    78148161   fd  Linux raid autodetect


```

i am not shure if i formated sdb1 right, - at one point i had 160gb listed under sda (not sda1)...

```

phil@workstation:~$ sudo fdisk /dev/sdb1

The number of cylinders for this disk is set to 9728.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdb1: 80.0 GB, 80023716864 bytes
255 heads, 63 sectors/track, 9728 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1        9728    78140128+  83  Linux


```

it is wierd to me that the partition id is 83, but fdisk -lu says fd (linux raid autodetect).

which harddrive do i mount when i just want one directory for two hds?

please help me out here - i am stuck! phil

---

### Post by tempo500 on 2006-09-29
ok... 
what i did...
sudo mkfs.ext3 /dev/mapper/sil_aebhajdccadg1
sudo mount /dev/mapper/sil_aebhajdccadg1 /media/sda

now i have it mounted with 140gb...
but
```

 sudo fdisk -lu

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
/dev/sda1              63   312592769   156296353+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sdb doesn't contain a valid partition table


```
whats with the partition table? is this ok this way?

---

### Post by tempo500 on 2006-09-30
please! i really need help on this!
i acadently formated the filesystem.... so now i am up running again but again i cant mount the raid.

1.) how should i format the drives? currently they are linux raid autodetect.

2.) which file should i mount? sil_blabla or sil_blabla1 sda/sda1 or sdb/sdb1

basically everything looks fine

dmraid -ay
```
RAID set "sil_aebhajdccadg" already active
RAID set "sil_aebhajdccadg1" already active

```
fdisk -lu
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
/dev/sda1              63   312592769   156296353+  fd  Linux raid autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   156296384    78148161   83  Linux

```

i still get an error when list the partition tabel in fdisk.is this my problem?oh.. it went away...
```
phil@workstation:~$ sudo fdisk /dev/mapper/sil_aebhajdccadg1

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/sil_aebhajdccadg1: 160.0 GB, 160047465984 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                         Device Boot      Start         End      Blocks   Id  System
/dev/mapper/sil_aebhajdccadg1p1               1        9728    78140128+  fd  Linux raid autodetect


```
it seems to me that i am so close!!! please help me! desperate, phil

---

