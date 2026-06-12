---
title: "Trying to install dual boot 14.04.1 on AlienwareX14 laptop with Windows 7"
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by webusr1 on 2014-07-26
Help. I'm struggling... I've been using Ubuntu for over 6 years, installed many times before the UEFI days, and I'm struggling to install 14.04.1 on this Dell Alienware X14 with Windows 7 Pro. I have performed SHRINK in Windows 7, created  147GB partition with Shrink, Formatted the 147GB patition with Gparted (EXT4 and reformated to EXT3). When I try to install Ubuntu 14.04.1, and boot off Ubuntu 12.04.1 DVD, the install sofware does not find my Windows 7 partition (sda1,2.3). The software wants to take over sda... I want to boot both Winddows 7 and Ubuntu 14.04.1. I've done this in the past with no problems....

fdisk output below and gpart output... Looks like the laptop was delivered with two hard drives (sda AND sdb). Any help would be greatly appreciated...


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38e744b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    21467135    10692608    7  HPFS/NTFS/exFAT
/dev/sda3        21467136  1646313471   812423168    7  HPFS/NTFS/exFAT
/dev/sda4      1646313472  1953523711   153605120   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38e74175

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    22081535    11039744    7  HPFS/NTFS/exFAT


AGAIN, any help would be greatly appreciated....

---

### Post by webusr1 on 2014-07-26
Also, see the install screen shot and notice that sda does not list the Windows 7 patitions and does not enable "Something Else" button.

---

### Post by oldfred on 2014-07-26
I would manually partition with gparted and create / (root) as 25GB, swap as 2GB if you have 4GB of RAM or more and /home as rest of 147GB. You would have to create all as logical partitions inside one extended partition.

Then use Something else and mount, & format those partitions during install. Then it should not modify NTFS partitions.

With Windows 8 this is a common issue, but that is from the fast boot or always on hibernation in Windows 8. Also if chkdsk needed which happens with a resize. Did you reboot Windows after resize?

Other issues are RAID or Intel SRT which looks like or is a RAID configuration or a gpt drive that installing Windows 7 over Windows 8 incorrectly converts to MBR(msdos).

 Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by webusr1 on 2014-07-26
I can only get 4 patitions on /dev/sda because Gparted doesn't let me create the swap partition or 5th partition (see the first thumbnail). However, the laptop has a 1TB 5400RPM SATA 6Gb/s + 80GB mSATA SSD Caching and I did discover that this laptop has a RAID ROM.  The ROM is the Intel Rapid Storage Technology Option ROM - 12.0.0.173 and has a BIOS console (Storage Manager Option ROM) that can be used with Windows and Linux based operating systems. The BIOS console itself is operating system independent.  So, the SATA drive is configured as /dev/sda and the SSD mSATS drive is configured as /dev/sdb on this laptop, I wonder if the RAID Config may be causing me problems even though the 1TB SATA drive is Non-RAID (See below). Looks like the mSATA SSD drive is configuured for RAID Stripe and Cache.

Here's the RAID Configuration below:
Disk Volumes
ID   Name                  Level                  Stripe  Size        Status  Bootable
0    Data_Volume   RAID(STRIPE)  128KB  10.5GB Normal  Yes
1     Data_Cache      RAID(CACHE) 128KB  64.0GB Normal  No

Physical Drives
ID   Device       Model  Size        Type/Status VOL ID        
0    ST1000LM  HN-M    931.5GB   Non-RAID Disk
1    LITEONIT   DMT-80  74.5GB    Cache Disk (1,2)

Here's the hardware below
Hard drive:Seagate ST1000LM ST1000LM024 HN-M
SSD: LITEONIT DMT-80M6M-11 mSATA 80GB

Another note, I did run CHKDSK /F after Shrinking the NTFS drive. I don't think the RAID config should be the issue with not detecting Windows 7 partitions on install because the SATA drive is non-RAID disk. Would you agree? And, if so... Any other work arounds?

---

### Post by ubfan1 on 2014-07-26
Your partitioning type of MSDOS only allows four primary partitions, so to add more, you have to delete the Linux partition, remake it as an extended partition (which counts as the fourth primary), and inside that extended partition, make the necessary logical partitions like swap, root, and home.

---

### Post by webusr1 on 2014-07-26
Okay, I was able to create the Extened Partition and inside the extended partition added swap and root. Re-run the install sesssion on USB this time; But, I still don't see the Windows partitions during the Ubuntu 14.04 Install session. I only see access to sda and also don't get the "something else" option. I've got the laptop Secure Boot disabled and I've tried booting Ubuntu Install DVD and USB in legacy mode and UEFI mode. Both modes (legacy and UEFI) give me the same results where I can Not detect the Windows partitions... See attached thumbnail for Gparted screenshot.

Any addition help would be greatly appreciated....Thanks.

---

### Post by webusr1 on 2014-07-26
TRIED GDISK, but not sure what to do with the error. Anyone an expert on GDISK as I'm not sure what commands to type into this tool? See below.
ran sudo gdisk -l /dev/sda

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory.
***************************************************************

Exact type match not found for type code DE00; assigning type code for
'Linux filesystem'
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9DA2D300-A9DC-45A3-8771-1159E4DFD693
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 7143 sectors (3.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63           80324   39.2 MiB    8300  Linux filesystem
   2           81920        21467135   10.2 GiB    0700  Microsoft basic data
   3        21467136      1646313471   774.8 GiB   0700  Microsoft basic data
   5      1953497088      1953523711   13.0 MiB    8200  Linux swap
   6      1646315520      1953495039   146.5 GiB   8300  Linux filesystem
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.8

Loading MBR data from /dev/sda

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

MBR command (? for help):

---

### Post by webusr1 on 2014-07-26
TRIED GDISK, but not sure what to do with the error. Anyone an expert on GDISK as I'm not sure what commands to type into this tool? See below.
ran sudo gdisk -l /dev/sda

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory.
***************************************************************

Exact type match not found for type code DE00; assigning type code for
'Linux filesystem'
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9DA2D300-A9DC-45A3-8771-1159E4DFD693
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 7143 sectors (3.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63           80324   39.2 MiB    8300  Linux filesystem
   2           81920        21467135   10.2 GiB    0700  Microsoft basic data
   3        21467136      1646313471   774.8 GiB   0700  Microsoft basic data
   5      1953497088      1953523711   13.0 MiB    8200  Linux swap
   6      1646315520      1953495039   146.5 GiB   8300  Linux filesystem
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.8

Loading MBR data from /dev/sda

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

MBR command (? for help):

---

### Post by oldfred on 2014-07-26
You did not want gdisk to convert to gpt partitioning. Your Windows 7 is installed in BIOS boot mode and Windows in BIOS mode can only boot from MBR(msdos) partitioned drives. 
Windows with UEFI can only boot from gpt partitioned drives.

Almost all systems I have seen with Intel SRT are UEFI boot from gpt partitioned drives.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

      
 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.


 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by webusr1 on 2014-07-27
Oldfred,
Problem is solved. Thanks for all the information. The solution was to wipe the drive and remove the Dell factory load (3 factory patitions removed) and re-install windows 7 from the DVD media, then Ubuntu installs as advertised detecting the Windows 7 patitions. Note that I had to boot using UEFI mode everytime I booted from DVD or USB. The Dell factory load does not have a UEFI partition (see the thumbnails above) and I think that's the main issue when trying to detect these Windows partitions during the Ubuntu install. Note that it doesn't  matter if you boot the DVD or USB device in legacy or UEFI mode, the Windows 7 patitions won't appear and "something else" does not exit during the Ubuntu install session. However, the next task is to get Intel Rapid Storage Technology enterprise for Windows 7 working and also Ubuntu OS using using the Linux MDADM application for Intel Matrix Storage. Hopefully, I can utilize SSD caching in both operating systems. Hope this info is helpful to someone else that has a new Dell computer and needs to dual boot Ubuntu with Windows7. Now I need to figure out how to mark this thread solved.

Thanks again, best regards, until next time!):P

---

### Post by oldfred on 2014-07-27
Some more links to see what others have done.
But I do not understand using SSD for cache. Ubuntu only needs 15 to 25GB for / (root) and will fully fit on the SSD for many of the larger SSD using SRT.
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
      
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)


  HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

---

### Post by webusr1 on 2014-07-28
Oldfred,
I've been configuring the Windows 7 (updating drivers) OS and testing this Alienware 14 laptop all day today and I've never seen Windows 7 perform so well with the 80GB SSD Cache drive utilizing the Intel Rapid Storage Technology with "Acceleration Mode" enabled. To confirm the performance difference, I disable the "Accelleration Mode" via the Intel Rapid Storage Technology software configuration. What I noticed was a typical Windows 7 that peformed averaged, and it took quite a while for the Windows desktop to be usable after logging into the user account (typical of Windows). Clicking on applications, browsing Internet (Firefox), performing ancillary file maintenance such as copying and moving files between different directories the system was not quick at all compared to my Ubuntu 14.04. After a couple of hours of testing, I enabled the Intel Rapid Storage Technology "Acceleration Mode". With "Acceleration Mode" enabled Windows 7 feels and performs twice as fast as Ubuntu 14.04. I am/was amazed!  I will be definitely be adding the Linux MDADM application to my Ubuntu 14.04 so that I can utilize the Intel Rapid Storage Technology. I hope to get the same performance boost with the "Acceleration Mode" enable in Ubuntu 14.04.

Note that I was also skeptic about utilizing an 80GB SSD drive as a cache drive at first and thought about loading Ubuntu 14.04 on this drive (this would mean disabling the RAID config and formatting the 80GB SSD), but I now understand how well the system performs with this SSD Cache drive configuration. The unique feature about this Alienware 14 laptop is that it is utilizing the Intel RAID ROM on the motherboard with the Intel Rapid Storage Technology software for the purposes of data redundancy and performance improvement. Regarding this SSD Cache approach or methodololgy and from what I understand or recall whenever the system requires or needs to locate data, it utilizes a hierarchy of different storage locations starting with the CPU cache,  and eventually working back to the hard drive. As the data is accessed through the difference peripheral devices (CPU Cache, RAM, Hard Drive), the speed of the storage gets slower. For example, accessing (read/write) data from the CPU cache is much faster than reading from the RAM and is much faster than reading directly from the hard drive. SSD caching adds an extra step between the RAM and hard drive, so the methodology becomes:

CPU Cache<-->RAM<-->SSD Cache<-->Hard Drive

Note with this approach, SSD drives are much faster than traditional hard drives, and provide the system a storage location which is much faster to access (read/write) data compared to a slow hard drive. That's my 100 ft explanation looking down at the system. It's not very technical, but that's a extermely high level with out getting into all of the proprietary details of the Intel Rapid Storage Technology. Wish me luck on getting Linux MDADM application working on my Ubuntu 14.04.

Best Regards!

---

### Post by oldfred on 2014-07-28
I added a 64GB SSD and have two installs of Ubuntu in 28GB / partitions. And it boots and loads applications really fast. But Linux caches recent activity in RAM so if you go back and reuse an app then it gets it from RAM.

Some with just 32GB SSD using SRT found that the SRT was configured to only use a small part of it, so they install / into a 16GB partition to make Ubuntu fast. Better to have entire system on SSD so you do not have to go back & forth.
Windows required vendor to make Windows boot in a few seconds, so they had to use hibernation and SSD cache to get Windows to boot. 
With an 80GB SSD, I do not understand why all of Windows is not on SSD?

---

### Post by webusr1 on 2014-07-29
[FONT=arial]Oldfred, thanks again for the info.... But, after two days, I have new problem... Windows7 partion is working, but Ubuntu 14.04 stop working. I can't boot it up...

Here's my symption. To get console messages I select Advance option and get the following message:

Please append a correct "root" boot option; here are the available partitions: Kernel Panic - not syncing: VFS : Unable to mount root fs on unknown-block(0,0)

Here's what I've tried:
1,  (Didn;t fix the problem)
Mount Ubuntu USB and run fsck /dev/sda4

2.  (Didn;t fix the problem)
sudo mount /dev/sda4 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt 
update-initramfs -u -k 3.13.0-32-generic
update-grub2

I went back and compared GDISK OUTPUTS since I've been documenting some this info and found that the GDISK output changed, but maybe it support to change. See the bold values of "First usable sector is 34, last usable sector is 1953525134" vs "First usable sector is 34, last usable sector is 1953523712" GDISK output after the successful Intall of Win7 and Ubuntu 14.04. This might be normal, but I don't know...

$ sudo gdisk -l /dev/sda

WROKING VERSION 
GPT fdisk (gdisk) version 0.8.8

Partition table scan:

  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 23E5278E-3ED9-4D4E-8C94-[/FONT]CB1891768CFD
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is **1953525134**
 Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          [206847   100.0]("tel:206847%C2%A0%C2%A0%20100.0") MiB   EF00  EFI system partition
    2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992      1543923711   736.0 GiB   0700  Basic data partition
   4      1543923712      1937141759   187.5 GiB   8300  
    5      1937141760      1953523711   7.8 GiB     8200  

NOT WORKING ANYMORE
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 23E5278E-3ED9-4D4E-8C94-CB1891768CFD
Partition table holds up to 128 entries

 First usable sector is 34, last usable sector is **1953523712**
Partitions will be aligned on 2048-sector boundaries

Total free space is 2015 sectors (1007.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          [206847   100.0]("tel:206847%C2%A0%C2%A0%20100.0") MiB   EF00  EFI system partition
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992      1543923711   736.0 GiB   0700  Basic data partition
   4      1543923712      1937141759   187.5 GiB   8300  
   5      1937141760      1953523711   7.8 GiB     8200  

ubuntu@ubuntu:/mnt/etc$

[FONT=arial black]
[FONT=arial]I tried to find this error message in logs with grep  on the var/logs... Maybe I'm looking in wrong location for logs...  Your help is greatly appreciated... I'm running with a Lieve 14.04 USB drive at this time.[/FONT]
[/FONT]

---

### Post by oldfred on 2014-07-29
Start up log is in /var/log.

 Change example sda4 to your Ubuntu partition
sudo mount /dev/sda4 /mnt
gksudo gedit /mnt/var/log/dmesg
or if you can boot to a terminal.
sudo nano /var/log/dmesg 

To see lots of details of install, run BootInfo report and post link it gives.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some give up & do a reinstall. Do not reinstall unless you use Something Else, see warning in link in my signature.

---

### Post by webusr1 on 2014-07-29
Boot Info below:

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => Windows 7/8/2012 is installed in the MBR of 
    /dev/mapper/isw_bjgdehigbd_Data_Volume.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 2038160 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys

isw_bjgdehigbd_Data_Volume1: ___________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992 1,543,923,711 1,543,454,720 Data partition (Windows/Linux)
/dev/sda4   1,543,923,712 1,937,141,759   393,218,048 Data partition (Linux)
/dev/sda5   1,937,141,760 1,953,523,711    16,381,952 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    22,081,535    22,079,488   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8032 MB, 8032092160 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62    15,683,519    15,683,458   c W95 FAT32 (LBA)


Drive: isw_bjgdehigbd_Data_Volume _____________________________________________________________________

Disk /dev/mapper/isw_bjgdehigbd_Data_Volume: 11.3 GB, 11306926080 bytes
255 heads, 63 sectors/track, 1374 cylinders, total 22083840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bjgdehigbd_Data_Volume1              2,048    22,081,535    22,079,488   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        561C-6912                              vfat       
/dev/sda3        F4F027D1F02798BE                       ntfs       
/dev/sda4        68276710-a6d3-4e29-a5f8-05299e17210c   ext4       
/dev/sdb1        468C15558C15413B                       ntfs       DATAPART1
/dev/sdc1        3F44-92B0                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev             /mnt/dev                 none       (rw,bind)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/pts         /mnt/dev/pts             none       (rw,bind)
/dev/sda4        /mnt                     ext4       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda4/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  68276710-a6d3-4e29-a5f8-05299e17210c
else
  search --no-floppy --fs-uuid --set=root 68276710-a6d3-4e29-a5f8-05299e17210c
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-68276710-a6d3-4e29-a5f8-05299e17210c' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  68276710-a6d3-4e29-a5f8-05299e17210c
    else
      search --no-floppy --fs-uuid --set=root 68276710-a6d3-4e29-a5f8-05299e17210c
    fi
    linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=/dev/sda4 ro  
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-68276710-a6d3-4e29-a5f8-05299e17210c' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-68276710-a6d3-4e29-a5f8-05299e17210c' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  68276710-a6d3-4e29-a5f8-05299e17210c
        else
          search --no-floppy --fs-uuid --set=root 68276710-a6d3-4e29-a5f8-05299e17210c
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=/dev/sda4 ro  
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-68276710-a6d3-4e29-a5f8-05299e17210c' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  68276710-a6d3-4e29-a5f8-05299e17210c
        else
          search --no-floppy --fs-uuid --set=root 68276710-a6d3-4e29-a5f8-05299e17210c
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic.efi.signed root=/dev/sda4 ro recovery nomodeset 
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=68276710-a6d3-4e29-a5f8-05299e17210c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=561C-6912  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda5 during installation
#UUID=64b99175-765b-4c58-a7ef-c73eeed8e169 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-5rfCalQ2/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-5rfCalQ2/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-5rfCalQ2/Tmp_Log: No such file or directory
File descriptor 9 (/proc/32030/mounts) leaked on lvscan invocation. Parent PID 9863: bash
File descriptor 63 (pipe:[91972]) leaked on lvscan invocation. Parent PID 9863: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-07-29__21h17 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 14.04.1 LTS, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="561C-6912" TYPE="vfat"
/dev/sda3: UUID="F4F027D1F02798BE" TYPE="ntfs"
/dev/sda4: UUID="68276710-a6d3-4e29-a5f8-05299e17210c" TYPE="ext4"
/dev/sdb1: LABEL="DATAPART1" UUID="468C15558C15413B" TYPE="ntfs"
/dev/sdc1: UUID="3F44-92B0" TYPE="vfat"

Windows not detected by os-prober on sda3.
Linux not detected by os-prober on sda4. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi

=================== /mnt/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Jul 22 22:21 grub.d
total 76
-rwxr-xr-x 1 root root  9424 May 15 19:02 00_header
-rwxr-xr-x 1 root root  6058 May  8 12:08 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15 19:02 10_linux
-rwxr-xr-x 1 root root 10412 May 15 19:02 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12 12:31 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15 19:02 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15 19:02 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15 19:02 40_custom
-rwxr-xr-x 1 root root   216 May 15 19:02 41_custom
-rw-r--r-- 1 root root   483 May 15 19:02 README




=================== /mnt/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
#TONY TEST
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== No kernel in /mnt/boot:
abi-3.13.0-32-generic
config-3.13.0-32-generic
efi
grub
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
System.map-3.13.0-32-generic
vmlinuz-3.13.0-32-generic
vmlinuz-3.13.0-32-generic.efi.signed


/boot/efi detected in the fstab of sda4: UUID=561C-6912   (sda1)
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda4    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    no-kernel,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:


                                                                          
Error: The backup GPT table is not at the end of the disk, as it should be.
This might mean that another operating system believes the disk is smaller.
Fix, by moving the backup to the end (and removing the old backup)?

                                                                          
Warning: Not all of the space available to /dev/sda appears to be used, you can
fix the GPT to use all of the space (an extra 1422 blocks) or continue with the
current setting?
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
1      1049kB  106MB   105MB   fat32        EFI system partition          boot
2      106MB   240MB   134MB                Microsoft reserved partition  msftres
3      240MB   790GB   790GB   ntfs         Basic data partition          msftdata
4      790GB   992GB   201GB   ext4
5      992GB   1000GB  8388MB


Model: ATA LITEONIT DMT-80M (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  11.3GB  11.3GB  primary  ntfs


Model: Kingston DataTraveler G2 (scsi)
Disk /dev/sdc: 8032MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  8030MB  8030MB  primary  fat32        boot, lba

=================== parted -lm:


                                                                          
Error: The backup GPT table is not at the end of the disk, as it should be.
This might mean that another operating system believes the disk is smaller.
Fix, by moving the backup to the end (and removing the old backup)?

                                                                          
Warning: Not all of the space available to /dev/sda appears to be used, you can
fix the GPT to use all of the space (an extra 1422 blocks) or continue with the
current setting?
BYT;
/dev/sda:1000GB:scsi:512:512:gpt:ATA ST1000LM024 HN-M;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot;
2:106MB:240MB:134MB::Microsoft reserved partition:msftres;
3:240MB:790GB:790GB:ntfs:Basic data partition:msftdata;
4:790GB:992GB:201GB:ext4::;
5:992GB:1000GB:8388MB:::;

BYT;
/dev/sdb:80.0GB:scsi:512:512:msdos:ATA LITEONIT DMT-80M;
1:1049kB:11.3GB:11.3GB:ntfs::;

BYT;
/dev/sdc:8032MB:scsi:512:512:msdos:Kingston DataTraveler G2;
1:31.7kB:8030MB:8030MB:fat32::boot, lba;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda4 on /mnt type ext4 (rw)
/dev on /mnt/dev type none (rw,bind)
/dev/pts on /mnt/dev/pts type none (rw,bind)
/proc on /mnt/proc type none (rw,bind)
/sys on /mnt/sys type none (rw,bind)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fb1 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 12 69 1c 56 4e  4f 20 4e 41 4d 45 20 20  |..).i.VNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 07 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 3f ff 5b 00 00 00 00  |.........?.[....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  be 98 27 f0 d1 27 f0 f4  |..........'..'..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff e7 50 01 00 00 00 00  |..........P.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  3b 41 15 8c 55 15 8c 46  |........;A..U..F|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  7.8G  131M  7.7G   2% /
/dev           none       7.8G   12K  7.8G   1% /mnt/dev
tmpfs          tmpfs      1.6G  1.3M  1.6G   1% /run
/dev/sdc1      vfat       7.5G  2.0G  5.6G  27% /cdrom
/dev/loop0     squashfs   939M  939M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      7.8G  1.4M  7.8G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      7.8G   80K  7.8G   1% /run/shm
none           tmpfs      100M   80K  100M   1% /run/user
/dev/sda4      ext4       185G  4.2G  171G   3% /mnt

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a8c82f9

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38e74175

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    22081535    11039744    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 8032 MB, 8032092160 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a145

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15683519     7841729    c  W95 FAT32 (LBA)


EFI detected. Please check the options.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!

You may want to retry after activating the [Backup and rename Windows EFI files] option.

=================== Default settings
Recommended-Repair
This setting would purge (in order to sign-grub upgrade version) and reinstall the grub-efi-amd64-signed of sda4, using the following options: upgrade-grub    kernel-purge   sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.
```

---

### Post by oldfred on 2014-07-29
Is your sdb the SRT, the script shows it is only using 12GB of the 80GB.
And when grub sees RAID (or the Intel SRT) it often has trouble correctly installing. But since it is on sda, it still should install.

You show this which we have seen with other Windows installs. I think the vendor uses an image from a smaller drive on a large drive.
Better to use gdisk to fix this.

       Use gdisk and verify partitions are correct with p, and use w to write the partition table. The v command can give more details on issues if necessary.  If not correct just use q to quit. The w -write should update primary, backup & protective MBR.

   sudo apt-get install gdisk
sudo gdisk /dev/sda
Command (? for help):

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by webusr1 on 2014-07-30
Oldfred,
I'm running out of time. I need to finish configuring this laptop for my kid so I can send it to college... Here's what happened....

Fixed Partition issue with GDISK (yea!), then fixed boot up issue with Boot Repair (yea!), but only Linux would operate. I lost functionality to windows 7. So, no big deal. Right??? I have all the windows7 media, and Ubuntu media... So, I decided to reload and blow away the RAID config and install windows 7 on SATA HD, and Ubuntu 14.04 mSATA SDD. Results, Windows 7 install behaves badly on SATA HD (won't boot unless I specific in BIOS after every boos), and Ubuntu 14.04 won't boot off mSATA SDD. Tried to fix with boot-repair, but no joy.

Since I'm pressed for time.... Here's where I crey "UNCLE!!!, my best Uncle" to EFI! I missed the old BIOS world...:( 
Wikipedia Credit: The Roman Empire theory says, Roman children, when beset by a bully, would be forced to say the Latin phrase, "Patrue, mi Patruissimo," or, "Uncle, my best Uncle," in order to surrender and be freed. Yes, I've surrendered to EFI.

So, the plan is: I'll be wiping both drives and boot to Legacy Mode, Install Windows 7, configure RAID as before, and get this laptop back to factory configuration. My college kid will have to use Ubuntu on USB FLASH DRIVE. I guess I'll need to make it persistant so data can be saved. This is real bummer, we've dual booted Linux and Windows since 1997 in this household. And, after we discovered Ubuntu the whole family fell in love with it because of its superiiority over windows. 

That's my forward plan. Thanks for all your help. I plan to buy a new motherboard and try to learn more about EFI when I have plenty of time.

Best Regards!

---

### Post by oldfred on 2014-07-30
If you buy a big larger flash drive you can do a full install to the flash drive, not a persistent install.

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I now only use gpt partitioning for all new drives, but do not plan on installing Windows on any of my drives. Ubuntu will boot in BIOS or UEFI mode from gpt drive.
Windows only boots in UEFI mode from gpt drive.
Both Windows & Ubuntu only boot in BIOS mode from MBR(msdos) drive.

This is my 32GB flash drive. I did not include swap and split it into / (root) and data.

```
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   fat32        EFI System  boot
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         sys

```

---

### Post by webusr1 on 2014-07-30
Thanks for that tip. I'll get a 32GB Flash drive tonight or tomorrow. Unfortunately, we live in world where it is a requirement to utilize windows. At home it's a Linux world, but outside of that we have to deal with reality. 

Cheers!

---

### Post by oldfred on 2014-07-30
I have used Kingston older one's and for last few years only bought Microcenter house brand flashdrives. They have them at checkout counter and store is too close. So every time I am there the price is cheaper. Last time USB3 was same or cheaper than my previous purchase. 
I only have USB2 ports but plan on new system soon. I did find USB3 flash drive was still about 10% faster with my USB2 ports.
I only use full install as emergency boot so I do not use regularly. Life may be an issue, so any data should be backed to another flash drive or hard drive.

 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

You also want to change settings to reduce writes as that is the slowest part of a flash drive. If you have a fair amount of RAM it is a bit slower loading, but once in RAM runs just as fast. But writes are really slow. I can do a full install to my SSD in under 15 min, but it takes over an hour to flash drive.

I use ext4 but turn journal off as partition is small. So no writes for journal. Trim is not supported on flash drives, but you can use noatime so that is not written on every file access.

---

