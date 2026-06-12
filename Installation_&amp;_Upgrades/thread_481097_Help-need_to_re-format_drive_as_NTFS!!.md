---
title: "Help-need to re-format drive as NTFS!!"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by denny14 on 2007-06-22
we have 2 hard drives, and have formatted them both, so each has one partition only. we installed Ubuntu on the first drive, and tried to install Vista on the second, but it won't let us, because it's not in NTFS format. How can we format the second drive as NTFS (bearing in mind Ubuntu is the only operating system currently installed?)

We tried formatting the second drive using the Vista and XP install discs, but both times it said something about it wasn't a valid windows hard drive (probably because it isn't in NTFS format.)

We need help please!
Thanks

we deleted the partition on the second drive (using the Vista and XP install discs), and then created a new partition, but it wouldn't let us install the Windows OS on it, in both cases.

---

### Post by scxtt on 2007-06-22
did you try using fdisk?
```
:> sudo fdisk /dev/hda
Password:

The number of cylinders for this disk is set to 4865.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081   83  Linux

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   **t   change a partition's system id**
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): L

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot   
 1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data    
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility   
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt         
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access     
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O        
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor      
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs        
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT        
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor      
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor      
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary  
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux raid auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep        
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT            
1c  Hidden W95 FAT3 75  PC/IX
```

---

### Post by cwgpress on 2007-06-22
> 
we deleted the partition on the second drive (using the Vista and XP install discs), and then created a new partition, but it wouldn't let us install the Windows OS on it, in both cases.

Here's something I'd try:
[LIST=1]
[*]boot into ubuntu
[*]run gparted
[*]Be sure you are on the correct device. Delete all partitions on it. Don't forget to write the changes to the disk.
[*]If there's an option to clear the mbr to some default state do that. I suspect the mbr is actually the problem
[*]Restart the system using the Windows install disk
[*]Let Windows partition and format as it sees fit
[/LIST]
If that doesn't work, find a way to low-level format the disk and then try the install.

Good luck!

---

