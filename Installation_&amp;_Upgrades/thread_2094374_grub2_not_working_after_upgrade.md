---
title: "grub2 not working after upgrade"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by Rockling on 2012-12-13
Just upgraded my dual boot winXP to Ubuntu 11.10 and now when the grub2 comes up and I can boot into ubuntu but when I select winXP it just falshes a blank screen before going back to the grub screen. So now I cant boot into Windows XP. below is the log from the boot info script. Any help would be great thanks.

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 260230130 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   253,987,649   253,907,325   7 NTFS / exFAT / HPFS
/dev/sda3         306,198,900   312,496,379     6,297,480  82 Linux swap / Solaris
/dev/sda4         253,987,650   306,198,899    52,211,250  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D5-0A17                              vfat       DellUtility
/dev/sda2        902099C32099B0A8                       ntfs       
/dev/sda3        3ca23b3f-386e-4ddb-993e-84a3a3c86789   swap       
/dev/sda4        e6c84b80-bcf2-4577-9a8f-41bb7b1adde0   ext2       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext2       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda4/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

---

### Post by oldfred on 2012-12-13
You installed grub to the Windows NTFS partition. That has to have a NTFS boot signature including which boot file ntldr(XP) or bootmgr(Vista/7/8) to use. It also has partition info like the partition table.

NTFS does keep a backup of the PBR - partition boot sector and testdisk can restore that from the backup if it is ok.

> sda2: _______________________________

File system: ntfs
[COLOR=Red]Boot sector type: Grub2 (v1.99)
Boot sector info: Grub2 (v1.99) is installed in the boot sector of sda2
and looks at sector 260230130 of the same hard drive
for core.img. core.img is at this location and looks
for on this drive. No errors found in the Boot[/COLOR]
Parameter Block.
Operating System: Windows XP
Boot files: /boot.ini /ntldr /NTDETECT.COM


Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by Rockling on 2012-12-14
Thanks Oldfred,

Using testdisk worked for me.

> This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawik...ms:Boot_Sector](http://sourceforge.net/apps/mediawik...ms:Boot_Sector)

Thanks

---

