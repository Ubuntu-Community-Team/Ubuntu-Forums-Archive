---
title: "Asus X54C came with Ubuntu, how to add dual boot?"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by jazz.h on 2012-09-14
Hi guys!
This cheap but excellent laptop came with Ubuntu 11.10 64bit pre-installed. It's hdd is 320 GB, 1st partition 2GB is hidden, 2nd ext3 300 GB.
It works great but I'd like to try Win7, too, as dual boot off course. 
- How should I do that without loosing hidden partition (if it's recovery, not swap), I'm not sure that win installer won't rewrite the hidden partition and make it active/boot?
- Can I loose my warranty if I mess something up and delete the hidden partition and preinstalled Ubuntu?
- Can I make a bootable dvd copy of the hidden partition?

I was thinking of accomplishing this in the following way:
1. Boot up with the latest Live usb Ubuntu iso image
2. Shrink the 2nd partition to 50 GB
3. Under unpartitioned space create partition ntfs 30 GB, for win7
4. Under remained space create another partition ntfs, for data as a shared partition between both OS.
5. Install win7 on 3rd partition as intended (this is critical, what will happen to a hidden part?)
6. Boot up again with the latest Live usb Ubuntu iso image, run grub-customizer and install grub to /dev/sda, it will add both entries at boot, probably hidden partition as well.

Any advice, am I doing something wrong?

---

### Post by oldfred on 2012-09-14
Best to post partition table.

sudo parted /dev/sda unit s print

Windows will only install to a NTFS primary partition formated NTFS. That partition has to have boot flag. This is for BIOS/MBR systems.

If UEFI its totally different.

---

### Post by jazz.h on 2012-09-15
thanks oldfred, here is the output:  

```
Number  Start      End         Size        Type     File system     Flags 
 1      2048s      3905535s    3903488s    primary  fat32           hidden, lba 
 2      3905536s   10123263s   6217728s    primary  linux-swap(v1) 
 3      10123264s  625141759s  615018496s  primary  ext4            boot
```

---

### Post by oldfred on 2012-09-15
What is FAT partition. I cannot tell if partitions aare gpt or MBR. 

This is full output, I show a efi partition as the first is fat32 with the boot flag in gpt partitioning, but my system is BIOS and I only created efi partition as I plan new system real soon now:

```
fred@fred-Precise:~$ sudo parted /dev/sde unit s print
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sde: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=Red]gpt[/COLOR]

Number  Start      End         Size       File system  Name     Flags
 1      2048s      616447s     614400s    fat32                 boot
 2      616448s    618495s     2048s                            bios_grub
 3      618496s    58925055s   58306560s  ext4         Precise
 4      58925056s  117229743s  58304688s  ext4         Quantal

```Since boot flag is on sda3, I assume you are MBR. You need to install Windows in a primary partition formated NTFS with the boot flag (active partition in Windows).
You may want to plan ahead a bit. If you use sda4 for Windows you have used all 4 primary partitions and cannot create any more. But when dual booting it may be best to also have a shared NTFS data partition so you are not writing into the Windows system partition. 
Often swap, Linux and data partitions are in logical partitions as Windows has to have a primary partition. But the extended partition that holds all the logicals counts as one of the 4 primary.

Be sure to have a Ubuntu liveCD to reinstall gru2's boot loader as Windows will overwrite the MBR.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jazz.h on 2012-09-15
Yes, the pertitions are MBR.
sda1 fat 2GB is hidden partition and it came with the laptop. When I mount it I can see these folders:

[boot]
[casper]
[install]
[isolinux]
md5sum.txt

So I assume this is not a recovery partition it's just Ubuntu 11.10 iso image which can be used to install OS again, but I can not see how in automatic way, cause there's no messages like "Press F9 to run recovery options" and so on... 
My biggest concern is should I delete this hidden partition or should I leave it intact, cause I would like to install the latest Ubuntu, but I'm not sure if it will damage my warranty at Asus? Would it be enough if I just burn it to dvd and delete it afterwards? 

Speaking theoretically now, if this pre-installed Ubuntu will have to be reinstalled, how would Asus suggest I do it using hidden sda1 cause there's no info on that in the manual, nor on the Asus site (I tried to find support or warranty info on Asus site regarding preinstalled Ubuntu OS, but no success so far).

I understood all the advices on max of 4 primary partitions, thanks.

---

### Post by oldfred on 2012-09-15
That looks like the same file structure as a USB flash drive to install Ubuntu. It probably is just an install partition like a USB flash drive would be.

Does it show up in grub as a bootable partition?

Or run Boot-Repair and see what it says in BootInfo, always useful to document system anyway:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by jazz.h on 2012-09-15
> Does it show up in grub as a bootable partition?This is a good question. 
I'll create bootinfo report, but can I see somehow if sda1 shows itself in grub as a bootable partition right now, I'm not able to run Boot Repair atm...?

---

### Post by oldfred on 2012-09-15
You can run Boot-Repair from any install, liveCD or USB. You can also download it as a bootable live repairCD.

---

### Post by jazz.h on 2012-09-17
Sorry for the delay oldfred.
Here is the relevant part of the boot report, I hope we can see weather automatics can recovery the system using files in hidden sda1 or it's just live iso image:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Testdisk is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 2660658 of the same hard drive for 
                       core.img. core.img is at this location and looks for  
                       on this drive. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 216054608 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:   Syslinux looks at sector 733576 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,905,535     3,903,488  1c Hidden W95 FAT32 (LBA)
/dev/sda2           3,905,536    10,123,263     6,217,728  82 Linux swap / Solaris
/dev/sda3    *     10,137,015    52,082,729    41,945,715  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B4A7-6668                              vfat       
/dev/sda2        79834c44-365b-4bca-abdb-ad7b3c2b3a88   swap       
/dev/sda3        b550a165-4db1-47d0-9ce6-a8e4e753ca78   ext4       
/dev/sdb1        8816-15FB                              vfat       New Volume

================================ Mount points: =================================

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7991675     3995807    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
phys=(1023, 125, 62) logical=(1022, 125, 62)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00001573

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3905535     1951744   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2         3905536    10123263     3108864   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3   *    10137015    52082729    20972857+  83  Linux
Partition 3 does not start on physical sector boundary.


Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7991675     3995807    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
phys=(1023, 125, 62) logical=(1022, 125, 62)
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdb is MSDos
sda1 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, with boot, /mnt/boot-sav/sda1, no-os, no-gpt, notEFItable, no-fstab.
sda3 : sda, not-sepboot, grub, aptget, 64, with boot, /mnt/boot-sav/sda3, with-os, no-gpt, notEFItable, fstab-without-efi.
sdb1 : sdb, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /live/image, no-os, no-gpt, notEFItable, no-fstab.
PARTED: Model: ATA TOSHIBA MK3259GS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
1      1049kB  2000MB  1999MB  primary  fat32           hidden, lba
2      2000MB  5183MB  3183MB  primary  linux-swap(v1)
3      5190MB  26.7GB  21.5GB  primary  ext4            boot



```

---

### Post by jazz.h on 2012-09-17
What I did before boot report is that I shrunk Ubuntu "/" partition sda3 from 300GB to 20GB, using gparted and it processed fine, Ubuntu can run again.
I'm thinking of leaving sda1 (if it's used for recovery) and delete sda2 and sda3. In the unpartitioned space I would install Windows (it will create 100mb sda2 for boot primary fat... and sda3 ntfs 50gb) then I would create 1 extended partition sda4 and inside of it 1 big data partition sda5 ntfs 250 GB and 1 ext4 partition sda6 20 GB for installing Ubuntu 12.04 in it, no swap).

---

### Post by oldfred on 2012-09-17
As configured, you have an unusual way to boot Linux. You have testdisk or a Window like boot loader that just chains to the boot flagged partition. Then grub2 is in the partition boot sector (PBR) to boot. 

Normally grub2 is not installed to a partition boot sector as it has to convert to blocklists or hard coded addresses. On major updates grub's files may get relocated on drive and then you would have to reinstall grub to the PBR. Normally grub2's boot loader is installed to the MBR of the drive.

Unless you want the older version of Ubuntu in the "recovery" partition, there is not much reason to save it. You can download newer versions and have a boot/repairCD or USB instead of the partition.

---

### Post by jazz.h on 2012-09-18
I deleted all the partitions except sda1, 2GB is not bothering me.   Then I installed Win7 on 50 GB sda3 as primary and win created sda2 100 MB primary for boot.   Then I created sda4 extended part, inside of it sda5 220 GB ntfs, sda6 20 GB ntfs, sda7 20 GB ext4.  Installed 12.04 into sda7, no swap, boot loader into /dev/sda.  Fine tweaked multiboot grub with grub-customizer.  When done with drivers in Win7 I saved win7 sda3 partition with CloneZilla and put the sda3 image into sda6 (along with the previous CloneZilla factory-whole-disc-image).  Finally, from Ubuntu I flagged sda6 as hidden.  Thanks oldfred!

---

