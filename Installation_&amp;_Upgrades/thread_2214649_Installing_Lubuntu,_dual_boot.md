---
title: "Installing Lubuntu, dual boot"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by zach.s on 2014-04-02
Hi!


My goal is to install Lubuntu 13.10 to a ATA ST3500320AS 465.76 GB hard drive. I chose Lubuntu with the intention of making an older computer run good(dell inspiron 530). 
This drive has the following partitions installed -


1.) FAT16 [SIZE: 86 MB]


2.) NTFS [SIZE: 20 GB]


3.) NTFS [SIZE: 426.1 GB]


4.) EXT4 [SIZE: 19.5 GB]




The fourth partition I made through "Minitool Partition Wizard Home Edition v7.5"


I follow these steps in order:


1.) Insert Lubuntu 13.10 cd and boot with selection of install


2.) The Welcome/Install screen appears and I select Continue with English language highlighted


3.) Next screen shows Preparing to install Lubuntu and explains requirements(drive space & connection to internet). I check download updates while installing & install this third party software. I select Continue


4.) Installation type screen appears. "This computer currently has no detected operating systems. What would you like to do?" I get options for erasing entire disk and install lubuntu, encrypt the new ubuntu installation for security, use LVM with the new ubuntu installation, or something else. I select something else. 


5.) This screen shows no partitions but 500.1GB of free space...


So in summary my problem is that I'm too dumb to understand why Lubuntu does not detect any of my partitions.


Any help or advice is much appreciated!! Thx!

---

### Post by oldfred on 2014-04-02
Post this from your live installer.
sudo parted -l

Since you already created ext4 partition, you may have to use Something Else or manual install. Auto install wants to create 2 partitions / (root) and swap but you have used all 4 primary partitions. Then you have to force an install without swap. If you delete current ext4 partition then auto install would create both / & swap inside one extended partition as logical partitions and then may work?

Is Windows hibernated or need chkdsk? After a resize Windows does need to run chkdsk and if you did not boot into Windows after resize you may just need to do that.

---

### Post by zach.s on 2014-04-02
Thanks oldfred for your reply)

I did the following steps:

1.) Booted Windows Vista
2.) Opened disk management
3.) Deleted Ext4 partition (unallocated 19.53GB) 
4.) Ran chkdsk 
5.) Booted Lubuntu and it still shows no partitions or operating systems.
6.) Executed sudo parted -l (It detects only my usb flash drive) : 

"
lubuntu@lubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? No                                                                


Model: USB DISK 2.0 (scsi)
Disk /dev/sdb: 4105MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End     Size    Type     File system  Flags
 1      512B   4105MB  4105MB  primary  fat32




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           


Error: /dev/zram0: unrecognised disk label                                


lubuntu@lubuntu:~$ "

I should also mention that I previously did an exact clone of another drive that was smaller to this drive. I've had no problems using windows or accessing the same data on this drive.

---

### Post by oldfred on 2014-04-02
How did you get gpt on your drive? 
The gpt partitioning scheme is newer and required with UEFI, Vista would not boot with UEFI (I think). 
Windows requires gpt partitioning to boot with UEFI. And only boots from gpt with UEFI.
Both Windows and Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.
Ubuntu will boot from gpt with BIOS or UEFI.

But if drive has both MBR & gpt, the Ubuntu installer gets confused on what you have or want and just fails. If drive is booting Vista in BIOS mode, you can use fixparts to remove old gpt backup partition table.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

