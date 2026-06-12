---
title: "Wubi, 10.10 AMD-64 &quot;no root filesystem&quot;"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by ledelato on 2011-10-30
While trying to install Ubuntu 10.10 (yes, I know it's a few versions behind and not LTS, but I've had minimal problems with it before) on a new computer using Wubi I've had the following happen:

1) Run Windows installer - get the error "pyrun.exe - No Disk There is no disk in the drive. Please insert a disk into drive". Click Continue repeatedly until the Wubi installer pops up and I install successfully.

2) Reboot computer

3)Choose Ubuntu from the boot menu

After Ubuntu boots, I get the error "no root file system is defined." I know this has been solved many times here, but the consensus seems to be to post the results of Boot Info Script and get help for my specific problems. I'm attaching the RESULTS.txt file from Boot Info Script.

Edit: I'm pasting results.txt into the body of the question as this seems to be standard practice.

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/mapper/pdc_bfhjfehf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

pdc_bfhjfehf1: _________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

pdc_bfhjfehf2: _________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

pdc_bfhjfehf3: _________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    33,556,479    33,554,432  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     33,556,480    33,761,279       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          33,761,280 1,953,388,543 1,919,627,264   7 NTFS / exFAT / HPFS


Drive: pdc_bfhjfehf _____________________________________________________________________

Disk /dev/mapper/pdc_bfhjfehf: 1000.1 GB, 1000137752576 bytes
255 heads, 63 sectors/track, 121593 cylinders, total 1953394048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_bfhjfehf1              2,048    33,556,479    33,554,432  27 Hidden NTFS (Recovery Environment)
/dev/mapper/pdc_bfhjfehf2   *     33,556,480    33,761,279       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_bfhjfehf3         33,761,280 1,953,388,543 1,919,627,264   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4CFE21E5FE21C7D2                       ntfs       PQSERVICE
/dev/sda2        1C5A22AF5A22861C                       ntfs       SYSTEM RESERVED
/dev/sda3        5EB224A5B224839D                       ntfs       Acer

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf sdg 



Some more info: My current OS is Windows 7 Pro x64. I've also had this problem when trying to install Ubuntu 11.10 and Linux Mint 11 (the newest version of Linux Mint).

---

### Post by ledelato on 2011-10-30
When trying to install from the CD (not using Wubi), I've gotten to the Allocate drive space screen and there are no options to install anywhere. I'm assuming this is related and hoping it will help someone guess the problem.

I'm attaching a picture of this screen.

Thanks!

---

### Post by bcbc on 2011-10-30
Do you have a fakeraid 0 or 1+0?

---

### Post by ledelato on 2011-10-30
If I do, I certainly didn't install it myself. This is a new PC with a 1 TB hard drive. The only partition-related thing I've done is use Windows Disk Management to shrink the 1 TB C:\ drive and make a 100 GB space to install Ubuntu. I later reversed this when I got the second error I described and decided to try Wubi.

I'm including all of the output from Windows System Information -> Storage

```

--DRIVES--
Drive	C:
Description	Local Fixed Disk
Compressed	No
File System	NTFS
Size	915.35 GB (982,849,155,072 bytes)
Free Space	543.37 GB (583,441,141,760 bytes)
Volume Name	Acer
Volume Serial Number	B224839D
	
Drive	D:
Description	CD-ROM Disc
	
Drive	F:
Description	Removable Disk
	
Drive	G:
Description	Removable Disk
	
Drive	H:
Description	Removable Disk
	
Drive	I:
Description	Removable Disk
	
Drive	J:
Description	CD-ROM Disc
	
Drive	K:
Description	Removable Disk
	
Drive	L:
Description	Removable Disk
	
Drive	Z:
Description	Network Connection
Provider Name	\\curie.iems.northwestern.edu\home

--DISKS--
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	WDC WD10EADX-22TDHB0 SCSI Disk Device
Bytes/Sector	512
Media Loaded	Yes
Media Type	Fixed hard disk
Partitions	3
SCSI Bus	0
SCSI Logical Unit	0
SCSI Port	0
SCSI Target ID	0
Sectors/Track	63
Size	931.45 GB (1,000,136,471,040 bytes)
Total Cylinders	121,593
Total Sectors	1,953,391,545
Total Tracks	31,006,215
Tracks/Cylinder	255
Partition	Disk #0, Partition #0
Partition Size	16.00 GB (17,179,869,184 bytes)
Partition Starting Offset	1,048,576 bytes
Partition	Disk #0, Partition #1
Partition Size	100.00 MB (104,857,600 bytes)
Partition Starting Offset	17,180,917,760 bytes
Partition	Disk #0, Partition #2
Partition Size	915.35 GB (982,849,159,168 bytes)
Partition Starting Offset	17,285,775,360 bytes
	
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	Generic- Compact Flash USB Device
Bytes/Sector	Not Available
Media Loaded	Yes
Media Type	Not Available
Partitions	0
SCSI Bus	Not Available
SCSI Logical Unit	Not Available
SCSI Port	Not Available
SCSI Target ID	Not Available
Sectors/Track	Not Available
Size	Not Available
Total Cylinders	Not Available
Total Sectors	Not Available
Total Tracks	Not Available
Tracks/Cylinder	Not Available
	
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	Generic- MS/MS-Pro/HG USB Device
Bytes/Sector	Not Available
Media Loaded	Yes
Media Type	Not Available
Partitions	0
SCSI Bus	Not Available
SCSI Logical Unit	Not Available
SCSI Port	Not Available
SCSI Target ID	Not Available
Sectors/Track	Not Available
Size	Not Available
Total Cylinders	Not Available
Total Sectors	Not Available
Total Tracks	Not Available
Tracks/Cylinder	Not Available
	
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	Generic- SD/MMC/MS/MSPRO USB Device
Bytes/Sector	Not Available
Media Loaded	Yes
Media Type	Not Available
Partitions	0
SCSI Bus	Not Available
SCSI Logical Unit	Not Available
SCSI Port	Not Available
SCSI Target ID	Not Available
Sectors/Track	Not Available
Size	Not Available
Total Cylinders	Not Available
Total Sectors	Not Available
Total Tracks	Not Available
Tracks/Cylinder	Not Available
	
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	Generic- SD/MMC USB Device
Bytes/Sector	Not Available
Media Loaded	Yes
Media Type	Not Available
Partitions	0
SCSI Bus	Not Available
SCSI Logical Unit	Not Available
SCSI Port	Not Available
SCSI Target ID	Not Available
Sectors/Track	Not Available
Size	Not Available
Total Cylinders	Not Available
Total Sectors	Not Available
Total Tracks	Not Available
Tracks/Cylinder	Not Available
	
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	Generic- SM/xD-Picture USB Device
Bytes/Sector	Not Available
Media Loaded	Yes
Media Type	Not Available
Partitions	0
SCSI Bus	Not Available
SCSI Logical Unit	Not Available
SCSI Port	Not Available
SCSI Target ID	Not Available
Sectors/Track	Not Available
Size	Not Available
Total Cylinders	Not Available
Total Sectors	Not Available
Total Tracks	Not Available
Tracks/Cylinder	Not Available
	
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	Motorola A855 USB Device
Bytes/Sector	Not Available
Media Loaded	Yes
Media Type	Not Available
Partitions	0
SCSI Bus	Not Available
SCSI Logical Unit	Not Available
SCSI Port	Not Available
SCSI Target ID	Not Available
Sectors/Track	Not Available
Size	Not Available
Total Cylinders	Not Available
Total Sectors	Not Available
Total Tracks	Not Available
Tracks/Cylinder	Not Available

--SCSI--
Name	AMD AHCI Compatible RAID Controller
Manufacturer	Advanced Micro Devices, Inc.
Status	OK
PNP Device ID	PCI\VEN_1002&DEV_4392&SUBSYS_04441025&REV_40\3&267A616A&0&88
I/O Port	0x0000C000-0x0000C007
I/O Port	0x0000B000-0x0000B003
I/O Port	0x0000A000-0x0000A007
I/O Port	0x00009000-0x00009003
I/O Port	0x00008000-0x0000800F
Memory Address	0xFE7FFC00-0xFE7FFFFF
IRQ Channel	IRQ 19
Driver	c:\windows\system32\drivers\amdsbs.sys (3.6.1540.127, 189.58 KB (194,128 bytes), 6/10/2009 3:37 PM)
	
Name	AMD RAID Console
Manufacturer	Advanced Micro Devices, Inc.
Status	OK
PNP Device ID	SCSI\PROCESSOR&VEN_AMD&PROD_RAID_CONSOLE\4&BA3C608&0&000A00
	
Name	Virtual CloneDrive
Manufacturer	Elaborate Bytes AG
Status	OK
PNP Device ID	ROOT\SCSIADAPTER\0000
Driver	c:\windows\system32\drivers\vclone.sys (5.4.4.3, 35.50 KB (36,352 bytes), 1/15/2011 10:21 AM)

--IDE--
this section is blank

```

---

### Post by bcbc on 2011-10-30
You probably have some fakeraid metadata that is confusing ubuntu.
Here's a post you can review - I don't know a lot about this so you'll have to figure out what's right: [http://ubuntuforums.org/showpost.php?p=10053893&postcount=17](http://ubuntuforums.org/showpost.php?p=10053893&postcount=17)

---

### Post by ledelato on 2011-10-30
Thanks! In the end, I did an install to a separate partition and not to Wubi.

Here was the solution:

1) Partition hard drive with Windows Disk Management

2) Boot into Ubuntu with the install CD

3) sudo dmraid -E -r /dev/sda

4) Install Ubuntu

The key was not restarting between steps 3 and 4. Originally, I was trying 2) -> 3) -> reboot, attempt to install with Wubi.

Again, thanks for your help.

---

