---
title: "Can't Install Grub2 on 2-HDD RAID"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by brennan2 on 2014-03-21
Hello all,

I am new to ubuntu and have read a lot about this problem, but it usually seems to be a unique fix, so sorry in advance if it isn't here. I am installing it on an old Dell XPS 410 (from a 14gb usb stick), but have installed ubuntu 13.10, and because the problem is with the bootloader I'm not sure if an older version will help. The former OS was windows 7.

During install I get the popular error:
> 
Unable to install GRUB in /dev/sda
Executing 'grub-install/dev/sda' failed
This is fatal error
OK


And consequently I can choose a list of partitions, or choose to skip installing the bootloader. So I skipped installing the bootloader,
rebooted from the USB, went to the "Try Ubuntu" option, and tried various fixes from the terminal. 

The closest I got was this: 

> The simplest way takes the form as follows from a terminal in a live cd session.

First mount the drive you have installed to:
sudo mount /dev/mapper/<yourRAIDPartition> /mnt

Then perform the grub and grub boot loader install with:
sudo grub-install --root-directory=/mnt/ /dev/mapper/<TheRAIDRoot>




I could mount properly, but the grub-install failed with the following errors:

> /usr/sbin/grub-bios-setup: warning: File system `ext-2' doesn't support embedding.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.

About the drives:
I have two different sized HDDs, one 320 GB HDD, one 1 TB HDD, and I have a striped RAID drive of 640 GB. I want to do a full install, without any other OS. There was a command to show partitions i believe (where control is first), and the first one after control is "/dev/mapper/isw_cabiabeggi_Volume0", so I believe the partition to use is "/dev/mapper/isw_cabiabeggi_Volume0p1"

sudo fdisk -l output:
> sudo fdisk -l
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xfe74 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036318

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             512      500223      249856   83  Linux
/dev/sda2          500734  1250275839   624887553    5  Extended
/dev/sda5   ?  3852968958  3513361443  1977679891    4  FAT16 <32M
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x0486 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e2e05

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      499711      248832   83  Linux
/dev/sdb2          501758  1953523711   976510977    5  Extended
/dev/sdb5   ?  1091548868  1091814794      132963+  7a  Unknown

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
247 heads, 25 sectors/track, 5073 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48dbd6f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2120    31326207    15662044    c  W95 FAT32 (LBA)

Disk /dev/mapper/isw_cabiabeggi_Volume0: 640.1 GB, 640141230080 bytes
255 heads, 63 sectors/track, 77826 cylinders, total 1250275840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00036318

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cabiabeggi_Volume0p1             512      500223      249856   83  Linux
/dev/mapper/isw_cabiabeggi_Volume0p2          500734  1250275839   624887553    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cabiabeggi_Volume0p5          500736  1250275839   624887552   8e  Linux LVM

Disk /dev/mapper/isw_cabiabeggi_Volume0p1: 255 MB, 255852544 bytes
255 heads, 63 sectors/track, 31 cylinders, total 499712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cabiabeggi_Volume0p1 doesn't contain a valid partition table
fdisk: unable to read /dev/mapper/isw_cabiabeggi_Volume0p2: Inappropriate ioctl for device


sudo parted -l output:
> ubuntu@ubuntu:~$ sudo parted -l
Error: Can't have a partition outside the disk!                           

Error: Invalid partition table on /dev/sdb -- wrong signature 486.        
Ignore/Cancel? ^C

Model: Generic Flash Disk (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1085kB  16.0GB  16.0GB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 636GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  636GB  636GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4228MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4228MB  4228MB  linux-swap(v1)


Error: /dev/mapper/isw_cabiabeggi_Volume0p5: unrecognised disk label      

Error: Can't have a partition outside the disk!                           

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cabiabeggi_Volume0p1: 256MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  256MB  256MB  ext2


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_cabiabeggi_Volume0: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size   Type      File system  Flags
 1      262kB  256MB  256MB  primary   ext2
 2      256MB  640GB  640GB  extended
 5      256MB  640GB  640GB  logical                lvm



Thanks very much in advance!

---

