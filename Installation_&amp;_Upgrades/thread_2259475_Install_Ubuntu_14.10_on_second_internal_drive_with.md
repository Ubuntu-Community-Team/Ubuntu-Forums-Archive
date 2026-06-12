---
title: "Install Ubuntu 14.10 on second internal drive with Win 7 on c drive Lenovo u430 Ideap"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by Eddie_Brown on 2015-01-04
Would like install Ubuntu on the built in 16GB SSd which is not used for Win7 as Win7 is installed on the main 500gb hdd (not in UEFi mode). When I try to install from USB flash drive it rejects the selected ssd drive. Any help appreciated please.

---

### Post by Dennis N on 2015-01-04
Not sure what you mean by "rejects the selected ssd drive." I would use the "Something else" option on the first installation screen and you should be able to choose a partition on your SSD to install Ubuntu on. Have you prepared partitions on the SSD before starting the install? You should do that first if you haven't. gparted is available in the installer.

---

### Post by fantab on 2015-01-04
It is very likely that the SSD is being used as a 'cacheing device'. You can [disable]("http://www.thewindowsclub.com/enable-disable-disk-write-caching-windows-7-8") it.
If you have an Intel board then check for [Intel SRT]("http://www.intel.com/support/chipsets/sb/CS-032826.htm") you'll have to disable it.
Also check in the BIOS for SATA mode, it should be set as AHCI.

If you can boot Ubuntu from DVD/USB (Try Ubuntu), then open Terminal [ctrl + alt + T] run the following command and post its output here:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by Eddie_Brown on 2015-01-05
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA LITEONIT LSS-16L (scsi)
Disk /dev/sda: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  16.0GB  16.0GB  fat32              msftdata


Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?   
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 16.0 GB, 16013942784 bytes
256 heads, 63 sectors/track, 1939 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xee59b4a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   473278463   236535808    7  HPFS/NTFS/exFAT
/dev/sdb3       473278464   976769023   251745280    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1988 MB, 1988100096 bytes
255 heads, 63 sectors/track, 241 cylinders, total 3883008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10e9cd17

---

### Post by Eddie_Brown on 2015-01-05
Get the message in text box

"NO ROOT FILE SYSTEM DEFINED
PLEASE CORRECT FROM PARTITIONING MENU"

Have posted screen info when I go into terminal and type the sudo parted -l and sudo fdisk -l commands

---

### Post by yancek on 2015-01-05
> "NO ROOT FILE SYSTEM DEFINED
PLEASE CORRECT FROM PARTITIONING MENU"

If you are getting this message during the attempt to install Ubuntu, you should see, if you are using the Somethng Else option, an Installation Type page.  On that page, you need to select the correct device and partition.  The output you posted shows the 16GB drive as sda and has one partition on it, sda1 which is formatted fat32.  That's a windows filesystem.  You need to change that to ext4 or some other Linux filesystem.  When you select the partition by highlighting it in the main window, click the Change tab and you should see an Edit partition window.  There is a "Mount point" option there and a drop down box to the right of it.  Select the "/" option, a forward slash signifying the root filesystem.

Make sure you get the right partition and the right drive as that might change, particularly if you remove and replace to different usb ports.

---

### Post by fantab on 2015-01-05
First check what's on the SSD...
> 1      1049kB  16.0GB  16.0GB  fat32              **msftdata**

> **msftdata** -- This flag identifies a [Microsoft Basic Data partition.]("http://en.wikipedia.org/wiki/Basic_data_partition") It normally holds a Microsoft filesystem, like FAT or NTFS, so such partitions will include your C:  partition and perhaps recovery or data partitions. You should not  delete or change them unless you understand precisely what type of data  is on the partition and want to delete it.

You can back up the partition as image with any windows parittion cloning/imaging tool as an option.

---

### Post by oldfred on 2015-01-05
Was this originally a Windows 8 system with Intel SRT, using sdb SSD as the cache. That uses RAID and drive was/is gpt.

You may need to remove the RAID info that Intel SRT uses.
       Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Run chkdsk on any NTFS partitions even if they currently work.

If you keep gpt on sdb, and want to boot in BIOS mode, you will need a tiny 1 or 2 MB unformatted partition on the gpt drive with the bios_grub flag. Otherwise grub will not install on a gpt drive correctly in BIOS mode.

---

### Post by Eddie_Brown on 2015-01-05
Yes it originally had Win 8 on it but decided to put Win7 on it, don't have a problem with Win 7 but thought it would be easy to put Ubuntu on the unused SSD drive and I've always wanted to get the hang of Ubuntu as it reminds me of the Osx on a Mac book I used to have but got to admit I think I'm out of my depth.

---

### Post by oldfred on 2015-01-05
Ever since Mac converted to Intel chips they use UEFI with gpt partitioning. But it is an older version of UEFI and does not (yet) have secure boot issues that Windows 8 has created.

---

