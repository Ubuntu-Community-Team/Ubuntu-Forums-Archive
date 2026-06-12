---
title: "Installing Ubuntu 14.04.2 on my Asus G751JY Windows 8.1 laptop"
date: 2015-03-04
forum: Installation &amp; Upgrades
---

### Post by Brandon5655 on 2015-03-04
Hello all,

I've already created a live usb disk but now I have no clue how to set my partitions to comfortably run Windows alongside Linux. I tried earlier and I kept getting a dev/sda fatal error so I thought it would be best to come here for the proper partitions to set to install my first Linux. Here is my system info including drive/partitions so you all can help me with a stable install of Linux. Thanks!

```
OS Name Microsoft Windows 8.1
Version 6.3.9600 Build 9600
Other OS Description  Not Available
OS Manufacturer Microsoft Corporation
System Name BRANDON-PC
System Manufacturer ASUSTeK COMPUTER INC.
System Model G751JY
System Type x64-based PC
System SKU ASUS-NotebookSKU
Processor Intel(R) Core(TM) i7-4860HQ CPU @ 2.40GHz, 2394 Mhz, 4 Core(s), 8 Logical Processor(s)
BIOS Version/Date American Megatrends Inc. G751JY.202, 9/10/2014
SMBIOS Version 2.7
Embedded Controller Version 255.255
BIOS Mode UEFI
BaseBoard Manufacturer ASUSTeK COMPUTER INC.
BaseBoard Model Not Available
BaseBoard Name Base Board
Platform Role Mobile
Secure Boot State Off
PCR7 Configuration Binding Not Possible
Windows Directory C:\Windows
System Directory C:\Windows\system32
Boot Device \Device\HarddiskVolume1
Locale United States
Hardware Abstraction Layer Version = "6.3.9600.17196"
User Name Brandon-PC\Brandon
Time Zone Pacific Standard Time
Installed Physical Memory (RAM) 32.0 GB
Total Physical Memory 32.0 GB
Available Physical Memory 30.3 GB
Total Virtual Memory 37.0 GB
Available Virtual Memory 35.3 GB
Page File Space 5.00 GB
Page File C:\pagefile.sys
Hyper-V - VM Monitor Mode Extensions Yes
Hyper-V - Second Level Address Translation Extensions Yes
Hyper-V - Virtualization Enabled in Firmware Yes
Hyper-V - Data Execution Protection Yes


Drive C:
Description Local Fixed Disk
Compressed No
File System NTFS
Size 213.91 GB (229,682,716,672 bytes)
Free Space 181.25 GB (194,615,820,288 bytes)
Volume Name OS
Volume Serial Number 30CF2C4A
 
Drive D:
Description Local Fixed Disk
Compressed No
File System NTFS
Size 233.03 GB (250,214,055,936 bytes)
Free Space 232.91 GB (250,083,987,456 bytes)
Volume Name 
Volume Serial Number 0B9705AD
 
Drive E:
Description Local Fixed Disk
Compressed No
File System NTFS
Size 232.86 GB (250,031,517,696 bytes)
Free Space 232.74 GB (249,901,457,408 bytes)
Volume Name 
Volume Serial Number 0FB710A3
 
Drive F:
Description Local Fixed Disk
Compressed No
File System NTFS
Size 12.02 GB (12,905,459,712 bytes)
Free Space 733.05 MB (768,663,552 bytes)
Volume Name Recovery
Volume Serial Number 80C9530E
 
Drive G:
Description CD-ROM Disc
 
Drive H:
Description Local Fixed Disk
Compressed No
File System NTFS
Size 232.83 GB (249,999,306,752 bytes)
Free Space 232.71 GB (249,869,246,464 bytes)
Volume Name 
Volume Serial Number 0FB71464
 
Drive I:
Description Local Fixed Disk
Compressed No
File System NTFS
Size 232.79 GB (249,956,302,848 bytes)
Free Space 232.67 GB (249,826,242,560 bytes)
Volume Name 
Volume Serial Number 0FB715E5
 
Drive J:
Description Local Fixed Disk
Compressed No
File System NTFS
Size 250.95 GB (269,459,562,496 bytes)
Free Space 250.83 GB (269,328,908,288 bytes)
Volume Name 
Volume Serial Number 0FBC1763

Description Disk drive
Manufacturer (Standard disk drives)
Model HGST HTS721010A9E630
Bytes/Sector 512
Media Loaded Yes
Media Type Fixed hard disk
Partitions 4
SCSI Bus 3
SCSI Logical Unit 0
SCSI Port 1
SCSI Target ID 0
Sectors/Track 63
Size 931.51 GB (1,000,202,273,280 bytes)
Total Cylinders 121,601
Total Sectors 1,953,520,065
Total Tracks 31,008,255
Tracks/Cylinder 255
Partition Disk #1, Partition #0
Partition Size 233.03 GB (250,214,056,960 bytes)
Partition Starting Offset 1,048,576 bytes
Partition Disk #1, Partition #1
Partition Size 232.83 GB (249,999,308,800 bytes)
Partition Starting Offset 250,215,105,536 bytes
Partition Disk #1, Partition #2
Partition Size 232.86 GB (250,031,520,768 bytes)
Partition Starting Offset 500,214,414,336 bytes
Partition Disk #1, Partition #3
Partition Size 232.79 GB (249,956,338,176 bytes)
Partition Starting Offset 750,245,935,104 bytes
 
Description Disk drive
Manufacturer (Standard disk drives)
Model SAMSUNG MZHPU512HCGL-00004
Bytes/Sector 512
Media Loaded Yes
Media Type Fixed hard disk
Partitions 4
SCSI Bus 0
SCSI Logical Unit 0
SCSI Port 0
SCSI Target ID 0
Sectors/Track 63
Size 476.94 GB (512,105,932,800 bytes)
Total Cylinders 62,260
Total Sectors 1,000,206,900
Total Tracks 15,876,300
Tracks/Cylinder 255
Partition Disk #0, Partition #0
Partition Size 46.07 MB (48,303,104 bytes)
Partition Starting Offset 1,048,576 bytes
Partition Disk #0, Partition #1
Partition Size 213.91 GB (229,682,718,720 bytes)
Partition Starting Offset 57,576,960 bytes
Partition Disk #0, Partition #2
Partition Size 250.95 GB (269,459,563,008 bytes)
Partition Starting Offset 229,740,904,448 bytes
Partition Disk #0, Partition #3
Partition Size 12.02 GB (12,905,463,808 bytes)
Partition Starting Offset 499,202,629,632 bytes
```

---

### Post by oldfred on 2015-03-05
I cannot tell from Windows data, but is Windows in UEFI or BIOS boot mode?
You have a new enough system that it is UEFI, but then Windows could be either.

Better to post this, from terminal in Ubuntu live installer.
sudo parted -l

If drive is gpt then it must be UEFI as Windows only boots from gpt with UEFI. If drive is MBR(msdos) then it must be BIOS.
Ubuntu will install to gpt partitioned drives with either UEFI or BIOS, but much better if installed in same boot mode as Windows.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
    [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It is a lot of info, but worth review. See link in my signature.

---

### Post by Brandon5655 on 2015-03-05
After doing a lot of research, I was able to install ubuntu!  Thanks everyone! However, I still do have another problem now that I've installed it. No Sound :( any quick fixes out there so I can watch the Youtubes with sound? lol Thanks

---

### Post by oldfred on 2015-03-05
Post a new thread with that in the title.
Someone may know issue, I have seen other threads which you also can search forum for.

---

