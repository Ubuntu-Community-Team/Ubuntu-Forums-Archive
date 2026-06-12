---
title: "fixing grub - windows and ubuntu dual boot"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by bobTurner on 2012-02-29
Hi,
Have a little issue with getting ubuntu and windows 7 working. 
This is what has happened. 
I had a 320GB harddrive which has my windows on and a 500GB harddrive with just data on. I shrunk the 500GB to allow for a 30GB partition for ubuntu,
I then installed ubuntu by selecting install alongside windows option from the live cd. 
It installed successfully, restarted then went into the OS selection screen where I selected Windows. Windows loaded fine and then I restarted. On restarting no OS selection screen appeared, instead it was just a flashing line. I followed some tutorials where they suggest pressing left shift but this just showed GRUB loading...

I have obtained these details from the live cd which I believe should be useful:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 625137663 
                       sectors, but according to the info from fdisk, it has 
                       1984 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 32776 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048   625,139,711   625,137,664  42 SFS
/dev/sda3         625,139,712   625,140,399           688  42 SFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   913,853,504   913,853,442   7 NTFS / exFAT / HPFS
/dev/sdb2         913,854,462   976,771,071    62,916,610   5 Extended
/dev/sdb5         913,854,464   968,384,511    54,530,048  83 Linux
/dev/sdb6         968,386,560   976,771,071     8,384,512  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8015 MB, 8015314944 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15654912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    15,654,911    15,654,849   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6010A7DE10A7BA04                       ntfs       
/dev/sdb1        AA3AE3803AE34841                       ntfs       Games
/dev/sdb5        b43e4505-ba6e-4f45-9797-c592c4c3171e   ext4       
/dev/sdb6        84ede393-8fe6-449d-9c4a-f408b95fc05e   swap       
/dev/sdc1        72A9-9B32                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /mnt                     ext4       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================


```

Thanks for any help :)

---

### Post by bobTurner on 2012-02-29
Forgot to mention I have tried using boot-repair and it is just stuck scanning my system.

---

### Post by oldfred on 2012-02-29
Script is showing SFS partitions which is Windows dynamic partitioning and Linux systems do not work with dynamic partitions. Some have reported that some Windows tools do not work with the dynamic partitions, so unless you really want them it may be better to convert back to basic. Windows converts to dynamic if you try to create more than the 4 primary partitions and per Microsoft it is a one way conversion. But third party tools may convert back, but have good backups it you want to do it. Previous posters have reported success with Mini-Tool and EASEUS, links below.

You have grub2's boot loader in sda1. As part of Windows repairs I would reinstall the Windows boot loader to sda and leave grub only on sdb. You can set BIOS to boot sdb and grub will let you boot Ubuntu or Windows (unless still dynamic).

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard MiniTool to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary

Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by YannBuntu on 2012-02-29
Hello

> **bobTurner said:**
> I have tried using boot-repair and it is just stuck scanning my system.

Please could you update Boot-Repair (version 3.16-0ppa10, will be available in ~2hours), then type "sudo boot-repair -d" in a terminal (Ctrl+Alt+T), and copy/paste here the output ? (this will show debugging information)

---

