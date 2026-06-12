---
title: "Several attempts to install Ubuntu alongside Win10... all failed."
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by mesmerized on 2016-02-16
Dear Users,

I'm a newbie when it comes to Linux, but I've decided to give it a shot and install Ubuntu alongside Win10. I've been following this guide step by step [http://www.pcsteps.com/3305-prepare-windows-dual-boot-installation/](http://www.pcsteps.com/3305-prepare-windows-dual-boot-installation/) but unfortunately for some reason not only does Ubuntu installation not offer the "alongside Windows" option, but what's even worse it doesn't see any of the partitions I created. I have two hard drives in my laptop - one is an mSSD drive where the OS is located and the other one is a regular HDD where I store data. 

Hope someone can help me out.

Thanks

---

### Post by Geoffrey_Arndt on 2016-02-16
OK,  . . . to start off any help thread, please provide the basics:

>   Your complete PC specs (make, model, cpu, ram, gpu info (what video chipset or system? nVidia, AMD, Intel, etc.))?
>   Why use a non-Ubuntu official documents guide? . . . that can be problematic from what we've seen on these forums.
>   Often, the "not-seeing" the Alongside option is because Windows fast-start/Hibernation has not been turned off.   Or . . . there is no recognizable space on the disks that Ubuntu can be installed into.    Ubuntu either requires "unformatted" or unallocated disk space (after shrinking the Windows "main" partition). Linux (Ubuntu) cannot be installed on a WIndows file system (fat32, ntfs, etc.).  If you do pre-setup a partition for Ubuntu, it should use an "ext4" linux filesystem.   Windows cannot do that.   Must use either the gparted program, or a Live CD like Parted Magic:

Note - best (safest) way to install is to NOT use Install Alongside, but to use custom install (the "Something Else" option on the installer).

[URL="http://partedmagic.com/?s=memtest"]http://partedmagic.com/?s=memtest




[/URL]

---

### Post by mesmerized on 2016-02-16
Thank you for your reply Geoffrey_Arndt

1. My PC specs: Gigabyte U2442 Ultrabook, i5-3210M 2.5GHz, 4GB RAM, GeForce 640M + Intell HD Graphics 4000, SSD Samsung Evo 120GB + HDD WD 500GB 7200RPM. 
2. Ubuntu official installation guide doesn't really offer any help in case the "install alongside Windows" option is missing. Nor does it say anything about how to handle the "something else" installation and creating partitions.
3. BIOS - Legacy OS. 
4. I switched off the fast-start option despite the fact that as far as I know it's only for UEFI? The hibernation option is unavailable.
5. I'd like to use the "something else" option, but the installer doesn't see any partitions and I don't know how to create them under Linux.

---

### Post by oldfred on 2016-02-17
If you have a BIOS install of Windows, have you used the 4 primary partitions. Or possibly converted to dynamic partitions?

Post these from live installer's terminal:
sudo parted -l
sudo fdisk -lu

---

### Post by mesmerized on 2016-02-18
> **oldfred said:**
> If you have a BIOS install of Windows, have you used the 4 primary partitions. Or possibly converted to dynamic partitions?

Post these from live installer's terminal:
sudo parted -l
sudo fdisk -lu

Thank you for your reply Oldfred.

Here are the results:

[U][B]1) sudo parted -l 
[/B][/U]
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000BPVT-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start  End    Size   File system  Name                  Flags
 1      135MB  500GB  500GB  ntfs         Basic data partition  msftdata




Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?                                                                   

I didn't know what to answer. It doesn't seem to see my SSD drive.


_**2) sudo fdisk -lu**_




ubuntu@ubuntu:~$ sudo fdisk -lu


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0958a42d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0dbd2c31


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   195627951    97812952    7  HPFS/NTFS/exFAT
/dev/sdb2       195629056   218157055    11264000    6  FAT16
/dev/sdb3       218157056   233519103     7681024    f  W95 Ext'd (LBA)
/dev/sdb4       233519104   234438655      459776   27  Hidden NTFS WinRE
/dev/sdb5       218159104   231061503     6451200    6  FAT16
/dev/sdb6       231063552   233519103     1227776    6  FAT16


Disk /dev/sdc: 31.0 GB, 30992891904 bytes
255 heads, 63 sectors/track, 3768 cylinders, total 60532992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    60532735    30265344    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by oldfred on 2016-02-18
Did you have a new Windows install and reinstalled Windows 7?
Windows has a bug on converting gpt partitioned drives to MBR(msdos).
New Windows uses UEFI/gpt, but default install of Windows 7 is BIOS/MBR.

Run fixparts on sdb to remove the backup gpt data.
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sdb

You also show gpt on sda, but only one NTFS partition?
Ubuntu will install to gpt partitioned drives for BIOS boot. If you want to install Ubuntu to sda, use Windows to shrink the NTFS partition and reboot Windows and run chkdsk on sda partition.

Best to have Ubuntu in BIOS boot mode as it lookes like Windows must be BIOS as sdb is MBR. And Windows only boots from MBR partitioned drives with BIOS.

---

### Post by mesmerized on 2016-02-18
> **oldfred said:**
> Did you have a new Windows install and reinstalled Windows 7?
Windows has a bug on converting gpt partitioned drives to MBR(msdos).
New Windows uses UEFI/gpt, but default install of Windows 7 is BIOS/MBR.

Run fixparts on sdb to remove the backup gpt data.
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sdb

You also show gpt on sda, but only one NTFS partition?
Ubuntu will install to gpt partitioned drives for BIOS boot. If you want to install Ubuntu to sda, use Windows to shrink the NTFS partition and reboot Windows and run chkdsk on sda partition.

Best to have Ubuntu in BIOS boot mode as it lookes like Windows must be BIOS as sdb is MBR. And Windows only boots from MBR partitioned drives with BIOS.

Thank you oldfred.

I upgraded my Windows 7 to Windows 10 a few days ago (which was an ordeal in itself) 
I have to say that all these 'gpt' and 'sda' abbreviations are a little bit difficult for me to understand. I'm not quite sure how to proceed now. Sorry, I've never had anything to do with Linux, but I'm eager to learn.

---

### Post by oldfred on 2016-02-18
Then you also need to understand the difference between Windows "drive" and partitions.
Windows confuses drive as it can be a physical drive like sda, or a partition like sda1, or sdb1.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
 Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

While you do not have UEFI, some definitions that cover MBR and gpt are at end of UEFI how-to thread linked in my signature below.

---

### Post by l6griffin on 2016-02-18
I'm sure glad I found this thread! I want to do the same as mesmerized dual boot with Win 10. I won't hi-jack this thread and start my own if required. I thought I was still a some what experienced computer, but with the advances in technology and MSF mucking around thank goodness for the information oldfred has provided. I'll exercise some patience and see if I can't get it right.

Eyes opened Larry

---

### Post by buzzingrobot on 2016-02-18
/dev/sda is the 500 gig drive and /dev/sdb is the Samsung SSD.   (In Linux, designations like "/dev/sda" refer to drives.)

parted found the SSD, but complained and asked a question before it was willing to list the partitions it found. fdisk also complained and then went on to list the partitions. (These are /dev/sdb1 through /dev/sdb6. In Linux, partitions get designations like /dev/sdb1/ /dev/sda1, on so on.  So, Linux sees the SSD drive as /dev/sdb, and finds 6 partitions on it.


If you want to put Ubuntu on the SSD, and use the 500-gig drive as a data drive for Ubuntu, you need to use Windows to reduce the space used by those 6 Windows partitions on the SSD to create enough room for Ubuntu. When I install Ubuntu here, about 20 gigs is used before I install anything else.  So, I'd opt for freeing up 30 gigs or so of space. The Ubuntu installer *should* see that free, unpartitioned space.

In Linux, the files we create are held in a "home" directory given the same name as the user we create during the install. That is, each Linux system has a single '/home' directory.  If Sally installs Linux and creates the "Sally" user for herself, then she will find a "Sally" directory is created in '/home':  '/home/Sally'. By default, files Sally creates and the configuration files that record the adjustments she makes to the applications she uses, will be stored in /home/Sally.

So, if the 500-gig drive is where you want the Linux files you create to be housed (as opposed to the Linux programs you install, which will go on the SSD), then you also need to free up space on the 500-gig drive.  

Linux also requires a swap partition, which I would also put on the 500-gig drive. There are probably a million different notions about the optimum size of a swap partition.  My idea here is to make it 4 gigs, the size of your RAM.

So, you need to clear enough room on the SSD to install the Ubuntu system, and you need to clear enough room on the 500-gig drive for the swap partition and the partition that will hold /home.  How big *that* needs to be is something you have to estimate based on how you use your computer.


Then, the Ubuntu installer *should* see this free space.  If you choose the "Something Else" option, it should see the SSD as /dev/sda and the 500-gig as /dev/sdb. You can create the swap partition on /dev/sdb and then allot the rest of the free space to /home.  The swap partition does not need to be formatted.  Choose "ext4" as the file system for /home.

The Ubuntu system on /dev/sda (the SSD) will be contained in a file tree identified simply as "/". Create a partition in the free space, then select "/" and "Ext4" as the file system.

Be sure to check that the installer has identified /dev/sda as the boot drive.

Be sure you check some of the threads here, and guidance elsewhere, about creating a dual boot system.

(All this complexity is because you're putting two different operating systems on one machine with multiple drives already in use by another OS.  Windows and OS X assume they have the entire machine at their disposal and hide the complexity.  Ubuntu will, in effect, do the same if you point the installer at an entire, empty, drive that's the only drive in the machine.)

---

