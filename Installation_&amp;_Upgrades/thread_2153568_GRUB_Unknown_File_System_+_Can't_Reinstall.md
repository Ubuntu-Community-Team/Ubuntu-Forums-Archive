---
title: "GRUB Unknown File System + Can't Reinstall"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by DutchGFX on 2013-06-11
Hey, so I installed Kali Linux over Backtrack 5. This booted alongside Ubuntu 11.10 and Windows 8 using GRUB. Now, GRUB boots up and goes into rescue mode, and pretty much whatever I type, it outputs Unknown File System.

I have tried Boot-Repair, and it couldn't install GRUB. I tried again, multiple times (after reboots) and it says Please CLose Package Managers. 

I ran the Bootinfoscript, here are my results. ```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       208,844       208,782  de Dell Utility
/dev/sda2    *        208,845    30,928,844    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,928,845   887,009,884   856,081,040   7 NTFS / exFAT / HPFS
/dev/sda4         887,011,326   976,773,119    89,761,794   5 Extended
/dev/sda5         887,011,328   929,241,087    42,229,760  83 Linux
/dev/sda6         931,291,136   970,352,639    39,061,504  83 Linux
/dev/sda7         970,354,688   976,773,119     6,418,432  82 Linux swap / Solaris
/dev/sda8         929,243,136   931,289,087     2,045,952  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        544E67124E66EBE4                       ntfs       RECOVERY
/dev/sda3        18B4B7BBB4B799A8                       ntfs       OS
/dev/sda5        6e0bacc8-e66e-473a-9964-6812ed6d20a0   ext4       
/dev/sda6        44a65e4f-a3fc-42cb-8b53-24d07a7c99ef   ext4       Kali
/dev/sda7        9a937876-5037-49a1-a28f-9f3ec0da1c0e   swap       
/dev/sda8        b518f4ae-6a68-46b8-92bb-305d0e548dfc   ext4       GRUB
/dev/sr0                                                iso9660    Ubuntu 12.04.2 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6e0bacc8-e66e-473a-9964-6812ed6d20a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9a937876-5037-49a1-a28f-9f3ec0da1c0e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/initrd.img-3.5.0-23-generic               2
               =                boot/vmlinuz-3.5.0-23-generic                  2
               =                boot/vmlinuz-3.5.0-23-generic.efi.signed       1
               =                initrd.img                                     2
               =                vmlinuz                                        2

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

My Windows 8 is on SDA3, Kali is suppossed to be on SDA6, Ubuntu on SDA5, and I had set asside SDA8 to try to install GRUB there, after it wouldn't install anywhere else, but it didn't work there, either. I have tried purging and reinstalling, it returns some error about unable to locate dev/sda or something of that nature. I have been trying to solve this probably a total of 8 hours so far, so I seak your assistance, thanks!

---

### Post by oldfred on 2013-06-14
You do not have grub anywhere. Most of grub is really inside your Ubuntu install, its boot loader should be in the MBR and it will have core.img in the sectors right after the MBR. 

Use Boot-Repair and the option to totally uninstall and reinstall grub2.

---

