---
title: "Boot problems after fstab edit"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by LouManChu on 2011-09-04
AMD Athlon64 3200+
PATA 250GB (boot drive)
SATA 500GB (secondary storage)

fdisk -l:
[B]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13c413c3

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaac165d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       27327   219504096    7  HPFS/NTFS
/dev/sdb2   *       27328       29877    20482875   83  Linux
/dev/sdb3           29878       30515     5124704+   f  W95 Ext'd (LBA)
/dev/sdb5           29878       30515     5124703+  82  Linux swap / Solaris

[/B]contents of /etc/fstab:
[B]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc  proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdb2 during installation
UUID=78e1f078-df6e-4bcf-8563-5d529082dbc2  /      ext3  errors=remount-ro    0  1  
# swap was on /dev/sdb5 during installation
UUID=edf0849c-28fe-4345-9028-0bdb5e0c9618  none   swap  sw                   0  0  
/dev/sdb1                                  /media/Main Storage  ntfs  defaults             0  0  
[/B]
My intention is to have the OS mount both hard drives and my dvd-burner at bootup so they are accessible from the get-go.  I hadn't actually changed anything in the file because I am still learning but ever since I opened it I can't boot properly.  I have confirmed that it is as it was by comparing the backup fstab file to the one used by the system.  My monitor wraps everything deep into the left side so I can't read all of it between post-BIOS and OS driver loading but I did get the following line 'could not be mounted /media/main and have figured out that S will skip or M will allow for a manual boot.  It's not bad compared to previous issues mentioned elsewhere but it is annoying to say the least.  I am going to try using boot-repair bootdisk but that looks like it's for machines using both Windows and Linux dual boot operations and this is a clean install of Ubuntu 11.04 only.  No other OS is installed.  It's interesting to me that Ubuntu recognizes my drives as SCSI devices but maybe that's a normal thing.

---

### Post by drs305 on 2011-09-04
> /dev/sdb1 /media/Main Storage ntfs defaults 0 0


If the mountpoint is supposed to be "Main Storage" then in fstab you can designate it as below so the space between Main and Storage is recognized.
> /dev/sdb1 /media/Main\040Storage ntfs defaults 0 0

The way it is currently listed, it is looking for /media/Main

For more detailed options for ntfs, please refer to the following thread by *bodhi.zazen*:
[Understanding Fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by LouManChu on 2011-09-04
That took care of that!  Thanks for the fix and for the links.
LMC

---

