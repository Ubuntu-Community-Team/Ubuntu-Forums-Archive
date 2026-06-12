---
title: "I need help creating a EXT3 Partition for a system drive clone"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by caffienda on 2007-02-04
I've been having a very hard time getting the search function to work for me, so please excuse me if this is answered.  I really need to get a 160GB drive set up with at ext3 partition. 

I am running Ubuntu 6.10.  I have the drive installed and it is HDB.  I need to make a partition so I can clone my current system as a backup to the newly installed drive.  I know that I will use "Fdisk /dev/hdb" as the command, but once I get into the , menu of "known partition types", EXT3 is not listed. 

The book I have says that I use the "mkfs.ext3" command and the "tune2fs /dev/hdb -j"  Which one is it


I've been told that this is the command that I'll use when I need to clone my system drive: 
sudo dd if=/dev/<partition to image> of=/path/to/image/file
I have the default Ubuntu partitioning, there is a /dev/hda1(ext3) and /dev/hda5 (swap)
Is this what I would enter if I wanted  to clone my system drive:
sudo dd if=/dev/hda1 of=/mnt/mynewlypartitionedHD/???

---

### Post by taurus on 2007-02-04
Do you have an empty partition you want to format it to ext3?

```
sudo fdisk -l
```

---

### Post by caffienda on 2007-02-04
this is what come up when I do fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19080   153260068+  83  Linux
/dev/hda2           19081       19457     3028252+   5  Extended
/dev/hda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


I would like to create an EXT3 partition on both hdb and hdc.  My problem is that I can't find the ext3 format when I'm in the fdisk menu, I type "l" to list known partition types and this is what I get:
> 
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

Do Ineed to install something before I can write a ext3 partition?

---

### Post by taurus on 2007-02-04
There's something wrong with your /dev/hdb drive!  You need to use cfdisk (or gparted in System -> Administration and of course, you need to install it first if you haven't done so) to create a partition for both /dev/hdb & /dev/hdc so they both would look something like /dev/hdb1 & /dev/hdc1, respectively.  Then, you can format them to ext3.

```
sudo cfdisk /dev/hdb
sudo cfdisk /dev/hdc
```

```
sudo mke2fs -j /dev/hdb1
sudo mke2fs -j /dev/hdc1
```

---

### Post by caffienda on 2007-02-04
Do you mean there is something physically wrong?  I recently did a complete wipe of the drive, zero'd it out with 3 passes.  I'm guessing this is why?

Could that explain the message, b/c it doesn't have a partition table?

---

### Post by caffienda on 2007-02-04
> **taurus said:**
> There's something wrong with your /dev/hdb drive!  You need to use cfdisk (or gparted in System -> Administration and of course, you need to install it first if you haven't done so) to create a partition for both /dev/hdb & /dev/hdc so they both would look something like /dev/hdb1 & /dev/hdc1, respectively.  Then, you can format them to ext3.

```
sudo cfdisk /dev/hdb
sudo cfdisk /dev/hdc
```

```
sudo mke2fs -j /dev/hdb1
sudo mke2fs -j /dev/hdc1
```


Ok, I'm still not sure what the # would be when selecting the type of filesystem when I run cfdisk.  it gives me a large selection of maybe 80+ types (FAT, FAT32, NTFS, Linux Swap, etc..)  No where does it list ext3.  This is what I need to know.  Does ext3 go by another name?  I see Linux swp is 82 and just plain Linux is 83.  Should I use 83 for ext3?

---

### Post by taurus on 2007-02-04
Yes, you should use 83 and then format it to ext3 from a terminal as I described above.  There is no ext3 in cfdisk.  You just want to tag it as Linux filesystem--83.

---

### Post by taurus on 2007-02-04
Wow!  Double post...

---

