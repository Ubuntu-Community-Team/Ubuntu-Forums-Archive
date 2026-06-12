---
title: "Lucid won't recognize external HDD"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by smain on 2010-03-22
Hi all

Just gotten new computer shipped with Win7 o.0.. anyway... I installed  lucid lynx beta on a second partition (and seperate hdd), so I could  dual-boot these two until 10.04 comes out in final (thats when its  goodbye windows)...

However... Lucid refuses to recognise my external HDD (it is NTFS)... It  simply just does not show up... no error message, no unmounted drive in  gparted... and can't seem to even find a /dev/sd* belonging to the  drive, using:

```
sudo fdisk -l /dev/sd*
```

The drive shows up and works without a  problem in Windows 7, also it worked on my previous computer running  Karmic...

Does anyone know what I have to do, to get the drive working in Lucid?

Jens

---

### Post by reiki on 2010-03-22
How is the external drive connected? USB? eSATA?

try sudo fdisk -l

try going to System -> Administration -> Disk Utility and see if it shows up in there.

---

### Post by smain on 2010-03-22
it is USB

It does not show up in Disk Utility

Just tested on my old computer again, no problem there, and also no problem on the Win7-partition on this computer o.0...

When the HDD is on sudo fdisk -l gives the following:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      120088   964499456    7  HPFS/NTFS
/dev/sda4          120088      121602    12157952    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0xc40f4ae1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          25      194560   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              25        1970    15625216   82  Linux swap / Solaris
/dev/sdb3            1970        8049    48828416   83  Linux
/dev/sdb4            8049      121602   912112640   83  Linux

```The /dev/sda is the Win7, and /dev/sdb is mu Ubuntu (they are on seperate internal HDD's)... As seen the extern HDD still does not show...

[EDIT]: The device might actually show up in disk utility... for a few moments a extern USB HDD showed up as /dev/sdg... however There was absolutely no way of mounting it since the option in disk utility was disabled/gone... and it disappeared from Disk Utility again suddenly before i tried mount command... Also now it disappears and reappears ind Disk Utility, about every 30 secs or so... still no mount button

[EDIT]: I have tried running af chkdsk /f on Win7... it did not find any problems with the HDD... I somehow suspect this might be a bug related to my two internal HDD's having the possibility of being in RAID, not sure why, however o_0

---

