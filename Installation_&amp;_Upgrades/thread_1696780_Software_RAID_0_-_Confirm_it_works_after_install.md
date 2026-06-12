---
title: "Software RAID 0 - Confirm it works after install?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by CiaoCiao on 2011-02-27
Quick and Dirty - Details later...

I installed a RAID 0 but had "problems".  Ubuntu and RAID appears to work, can boot, no error messages.  Gparted reports problems on the md0 as well as sda and sdb. Couldn't find valid filesystem superblock. among others..
I have no experience with RAID, and, aside from gparted, am unsure how to test that a RAID system works?  Ideas?



A "short" history..
Asus M488TD-V EVO/US3 which has a BIOS RAID.
I used BIOS to create RAID 0 2 x 2 TB drives, which created a 4 TB RAID 0.  However Ubuntu installer (live and alternate) both reported the hardware RAID to be 1.8 (or so) TB....Couldn't find out any reason why, but after much reading dropped the hardware idea and installed ALternate Ubuntu 10.10 CD with software RAID, as per [_this_]("http://www.youtube.com/watch?v=-x2rZe2Z9as") tutorial video.

So I innocently simply disabled the RAID option in BIOS and changed to IDE for the SATA drives... (For the record, this is not correct!  My hardware raid was still active, and ubuntu let me create a software RAID on top of this.)  The system was unable to boot and would hang.

When I realized what was wrong I re-enabled the hardware RAID, went through the BIOS utility to delete the RAID, then disabled the RAID in BIOS again.

The alternate installer has a Rescue option, which let me go to a command prompt for the / partition.  I doubt this had much affect, just for FYI..

Rebooting the system and selecting the drive which has a non-RAID /boot partition seemed to work no problems.  

Thanks for reading and any ideas...

CiaoCiao

---

### Post by CiaoCiao on 2011-02-27
some output from my system...

```
hubert@fureys64:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md0              38445384   2549260  33943056   7% /
none                   3927880       312   3927568   1% /dev
none                   3967956       104   3967852   1% /dev/shm
none                   3967956        92   3967864   1% /var/run
none                   3967956         0   3967956   0% /var/lock
none                  38445384   2549260  33943056   7% /var/lib/ureadahead/debugfs
/dev/sda1               472036     30702    416963   7% /boot
/dev/md2             3802468024    228172 3609085608   1% /home
hubert@fureys64:~$ fdisk -l /dev/md0
Cannot open /dev/md0
hubert@fureys64:~$ sudo fdisk -l
[sudo] password for hubert: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

Disk /dev/md1: 3999 MB, 3999137792 bytes
2 heads, 4 sectors/track, 976352 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 40.0 GB, 39998849024 bytes
2 heads, 4 sectors/track, 9765344 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md2: 3955.8 GB, 3955798966272 bytes
2 heads, 4 sectors/track, 965771232 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

```

---

### Post by towheedm on 2011-02-27
Firstly, I had the same and continue to have the same problem booting from a RAID1 partition.  I' also booting from a non-RAID /boot partition.  You cannot boot from a RAID0 partition but should be able to boot from a RAID1.  Tried for about 3 hours on Saturday but it still failed to boot from the RAID1 /boot partition.

I'm assuming the RAID0 partitions were marked as raid partitions.  The RAID0 drives will looked smaller after formatting because of space being used for the superblock and other filesystem internals.  This is normal.

Now after you created the RAID 0 partition from /dev/sdax and /dev/sdbx, the superblocks no longer exists as it is now part of a RAID 0 device (/dev/md0 in your case) and so GParted will have these partitions marked as invalid or without a filesystem.  DO NOT depend on GParted for checking RAID devices.

You can use the palimpset utility to check your raid devices.  On the left pane you should see a list of you Multi-Disk devices.  Select one and on the right side it allows several options, one to check and even benchmark the raid device.\

---

### Post by CiaoCiao on 2011-02-27
It was right under my nose...Thanks for the advice, I'll check into it..

---

### Post by psusi on 2011-02-27
Actually grub2 can boot from raid0 just fine.

Can you post the output of sudo parted print?

---

### Post by CiaoCiao on 2011-02-28
I did something wrong?

```
hubert@fureys64:~$ sudo parted print
[sudo] password for hubert: 
Error: Could not stat device print - No such file or directory.           
Retry/Cancel? r                                                           
Error: Could not stat device print - No such file or directory.           
Retry/Cancel? c
hubert@fureys64:~$ sudo parted
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) help print                                                       
  print [devices|free|list,all|NUMBER]     display the partition table,
        available devices, free space, all found partitions, or a particular
        partition

	Without arguments, 'print' displays the entire partition table. However
        with the following arguments it performs various other actions.
          devices   : display all active block devices
          free      : display information about free unpartitioned space on the
        current block device
          list, all : display the partition tables of all active block devices
          NUMBER    : display more detailed information about this particular
        partition
(parted) quit                                                             
hubert@fureys64:~$ sudo parted print all
Error: Could not stat device print - No such file or directory.           
Retry/Cancel? c                                                           
hubert@fureys64:~$ 

```

---

### Post by YesWeCan on 2011-02-28
I'm not sure I really understand what the question is, but...

Grub2 will not boot a RAID array if installed in a GUID partition.

This is because Grub2 needs a pile of code to be able to read a RAID. This code is normally installed in a 30kB area just behind the MBR in a DOS partition table formatted disk. This disk area is not available to Grub2 in a GUID partition table disk.

It is recommended to create a 1MB (non-RAID) "BIOS boot partition" on a GUID for its core.img file.
See: [https://wiki.archlinux.org/index.php/GUID_Partition_Table](https://wiki.archlinux.org/index.php/GUID_Partition_Table)

---

### Post by towheedm on 2011-02-28
> **YesWeCan said:**
> I'm not sure I really understand what the question is, but...

Grub2 will not boot a RAID array if installed in a GUID partition.

This is because Grub2 needs a pile of code to be able to read a RAID. This code is normally installed in a 30kB area just behind the MBR in a DOS partition table formatted disk. This disk area is not available to Grub2 in a GUID partition table disk.

It is recommended to create a 1MB (non-RAID) "BIOS boot partition" on a GUID for its core.img file.
See: [https://wiki.archlinux.org/index.php/GUID_Partition_Table](https://wiki.archlinux.org/index.php/GUID_Partition_Table)

Actually, when I did it, it was msdos not gpt.  Still no dice booting from RAID1 or 0.

---

### Post by CiaoCiao on 2011-03-05
Well it wasn't for lack of trying....

I am unable to check RAID array when booted into Ubuntu 10.10 on my HDD RAID0, since I get error message Error checking array: helper exited with exit code 1: device /dev/md1 is not idle

I boot using the live CD and install mdadm, but when I try to start a RAID array I get error message not enough installed componants...

When I make a USB boot drive and try to install mdadm, the USB flash drive is no longer bootable and I get error messages with installing some other packages.  Believe it is related to [[COLOR="RoyalBlue"]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023") bug.  I tried workarounds listed but always end with an unbootable USB flash device.

My raid and everything appears to be working since I haven't encountered any problems, so I'll mark as resolved..

Anyone with any ideas or suggestions please post, I'll definitely follow up.. 

Cheerios..

---

