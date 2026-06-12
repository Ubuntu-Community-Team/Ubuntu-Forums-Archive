---
title: "grub sata raid aware ?"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by synrat on 2007-10-30
I have Abit AB9 Pro motherboard with a bunch of SATA chipsets, with 4 drives plugged into ports 0,1,4,5 of the main Intel controller ( isw ), which operates in RAID mode. 
The first 2 drives, 0 and 1 are my Linux drives, md mirrored. No problem there. 
The other 2 drives , 4 and 5 are hardware raid mirrored and have Vista installed.
 
Now, in the past ( before going with Raid for Windows ) I've had no problems booting Windows from whichever drive by simply remapping devices in menu.lst/devices.map,
but I think now I'm faced with a new problem - getting grub to see the raid volume. 
Linux itself sees and happily mounts /dev/mapper/isw_djfaigjege_Volume01, after simply installing dmraid ( I love simple after Slackware :).  

I tried setting up grub manually by telling it that 'device (hd2,0) is actually /dev/mapper/isw_djfaigjege_Volume01' and saving that config to hd0 ( leaving Windows partition and boot alone ), but that didn't help.  
Is there anything else to be done to get dual boot working in this setup or is my only choice  to swap the cables each time I want to boot Windows ? :).

Thanks a lot in advance.

---

### Post by Selfish Meme on 2007-10-31
First read this [https://help.ubuntu.com/community/FakeRaidHowto#head-6c76652aaaf5e147adaaca8b0547d2dd06f2c5ce](https://help.ubuntu.com/community/FakeRaidHowto#head-6c76652aaaf5e147adaaca8b0547d2dd06f2c5ce)

and then the end of your menu.lst should look like this (windows is in partition 1 on my system)

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

you must run

# setup grub

after you have finished modifying menu.lst

---

### Post by synrat on 2007-10-31
Thank you for you reply, but I'm not sure you understood.  I'd done that already, but my problem was that grub wasn't seeing any device mappings such as /dev/mapper/isw........ and hence no matter what I put in device.map file, it wasn't booting stuff from the sata raid partition where windows is, eventhough I remapped it. 


root (hd2,0)
rootnoverify (hd2,0)
makeactive
map (hd2)  (hd0)
map (hd0)  (hd1)
map (hd1)  (hd2)
chainloader +1 

and device.map has

/devsda (hd0)
/dev/sdb (hd1)
/dev/mapper/isw_diskname (hd2)

---

### Post by meierfra on 2007-11-01
the device map is not used at boot-up. So editing the device.map will not make any difference.

Try

rootnoverify  (hd2,0)
makeactive
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1

If that didn't work, post your menu.lst and the output of "sudo fdisk -l"

---

### Post by synrat on 2007-11-03
I tried that too. it didn't work.


sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d4838

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4255    34178256   fd  Linux raid autodetect
/dev/sda2            4256       24194   160160017+  fd  Linux raid autodetect
/dev/sda3           24195       24321     1020127+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00029b24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4255    34178256   fd  Linux raid autodetect
/dev/sdb2            4256       24194   160160017+  fd  Linux raid autodetect
/dev/sdb3           24195       24321     1020127+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd33df4b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244193280    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd33df4b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244193280    7  HPFS/NTFS

Disk /dev/md0: 34.9 GB, 34998452224 bytes
2 heads, 4 sectors/track, 8544544 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 164.0 GB, 164003774464 bytes
2 heads, 4 sectors/track, 40039984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/dm-0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/dm-0: 250.0 GB, 250056015872 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd33df4b8

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       30401   244193280    7  HPFS/NTFS

Disk /dev/dm-1: 250.0 GB, 250053918720 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong dsudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d4838

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4255    34178256   fd  Linux raid autodetect
/dev/sda2            4256       24194   160160017+  fd  Linux raid autodetect
/dev/sda3           24195       24321     1020127+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00029b24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4255    34178256   fd  Linux raid autodetect
/dev/sdb2            4256       24194   160160017+  fd  Linux raid autodetect
/dev/sdb3           24195       24321     1020127+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd33df4b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244193280    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd33df4b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244193280    7  HPFS/NTFS

Disk /dev/md0: 34.9 GB, 34998452224 bytes
2 heads, 4 sectors/track, 8544544 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 164.0 GB, 164003774464 bytes
2 heads, 4 sectors/track, 40039984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/dm-0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/dm-0: 250.0 GB, 250056015872 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd33df4b8

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       30401   244193280    7  HPFS/NTFS

Disk /dev/dm-1: 250.0 GB, 250053918720 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
evice.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by synrat on 2007-11-06
anyone ?

---

### Post by psusi on 2007-11-08
"It does not work" is not an error description.  You need to be VERY specific about what goes wrong.  

Also I think your grub commands should be:

map (hd2) (hd0)
rootnoverify (hd0,1)
chainloader +1


Remember, grub numbers partitions from 1, not 0.

---

