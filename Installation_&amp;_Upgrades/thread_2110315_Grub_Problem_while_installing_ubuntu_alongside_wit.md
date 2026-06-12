---
title: "Grub Problem while installing ubuntu alongside with Windows&#65311;"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by chenxigrace on 2013-01-29
I am a beginner for linux and have so many trouble installing ubuntu. Is there anyone can help me? I choose to install ubuntu alongside win 7. But the boot loader install has failed. When I restart, it shows :

GNU GRUB version 1.99-21ubuntu3.1

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

Maybe I have to install grub? which partition should I install and how?

I have tried boot_info_script, the result is ```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdc.
 => No boot loader? is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/mapper/isw_bhiddahgdf_ARRAY.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:  Syslinux looks at sector 1429961 of /dev/sdc4 for its 
                       second stage. SYSLINUX is installed in the /isolinux 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

isw_bhiddahgdf_ARRAY1: _________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

isw_bhiddahgdf_ARRAY2: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

isw_bhiddahgdf_ARRAY3: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, 
                       isw_bhiddahgdf_ARRAY3 starts at sector 0. But 
                       according to the info from fdisk, 
                       isw_bhiddahgdf_ARRAY3 starts at sector 362153295.
    Operating System:  
    Boot files:        

isw_bhiddahgdf_ARRAY4: _________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

isw_bhiddahgdf_ARRAY5: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, 
                       isw_bhiddahgdf_ARRAY5 starts at sector 63.
    Operating System:  
    Boot files:        

isw_bhiddahgdf_ARRAY6: _________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /etc/fstab /boot/grub/core.img

isw_bhiddahgdf_ARRAY7: _________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       273,104       273,042  de Dell Utility
/dev/sda2    *        273,105   362,153,294   361,880,190   7 NTFS / exFAT / HPFS
/dev/sda3         362,153,295   566,949,914   204,796,620   7 NTFS / exFAT / HPFS
/dev/sda4         566,949,976   976,552,447   409,602,472   f W95 Extended (LBA)
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.

/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4051 MB, 4051697664 bytes
255 heads, 63 sectors/track, 492 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc4    *             63     7,913,471     7,913,409   b W95 FAT32


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 8014 MB, 8014528512 bytes
41 heads, 9 sectors/track, 42421 cylinders, total 15653376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  32    15,646,719    15,646,688   b W95 FAT32


Drive: isw_bhiddahgdf_ARRAY _____________________________________________________________________

Disk /dev/mapper/isw_bhiddahgdf_ARRAY: 500.0 GB, 499994853376 bytes
255 heads, 63 sectors/track, 60787 cylinders, total 976552448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bhiddahgdf_ARRAY1                 63       273,104       273,042  de Dell Utility
/dev/mapper/isw_bhiddahgdf_ARRAY2   *        273,105   362,153,294   361,880,190   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bhiddahgdf_ARRAY3        362,153,295   566,949,914   204,796,620   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bhiddahgdf_ARRAY4        566,949,976   976,552,447   409,602,472   f W95 Extended (LBA)
/dev/mapper/isw_bhiddahgdf_ARRAY5        566,949,978   929,998,258   363,048,281   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bhiddahgdf_ARRAY6        929,998,336   970,330,111    40,331,776  83 Linux
/dev/mapper/isw_bhiddahgdf_ARRAY7        970,330,624   976,552,447     6,221,824  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_bhiddahgdf_ARRAY1 07D8-0C04                              vfat       DellUtility
/dev/mapper/isw_bhiddahgdf_ARRAY2 8C0ADA1C0ADA035E                       ntfs       
/dev/mapper/isw_bhiddahgdf_ARRAY3 01C9D8A543878C50                       ntfs       
/dev/mapper/isw_bhiddahgdf_ARRAY5 01C9D8A54462F830                       ntfs       
/dev/mapper/isw_bhiddahgdf_ARRAY6 e5ee7216-4ce5-4900-b232-48aa45ea9847   ext4       
/dev/mapper/isw_bhiddahgdf_ARRAY7 1b716b14-75a0-4779-86a0-01b363af1085   swap       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc4        B4FE-5315                              vfat       Ubuntu 12.0
/dev/sdd1        3007-0D67                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bhiddahgdf_ARRAY
isw_bhiddahgdf_ARRAY1
isw_bhiddahgdf_ARRAY2
isw_bhiddahgdf_ARRAY3
isw_bhiddahgdf_ARRAY4
isw_bhiddahgdf_ARRAY5
isw_bhiddahgdf_ARRAY6
isw_bhiddahgdf_ARRAY7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc4        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdd1        /media/3007-0D67         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


======================= isw_bhiddahgdf_ARRAY6/etc/fstab: =======================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bhiddahgdf_ARRAY6 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bhiddahgdf_ARRAY7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=========== isw_bhiddahgdf_ARRAY6: Location of files loaded by Grub: ===========

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/initrd.img-3.2.0-29-generic-pae           3
               =                boot/vmlinuz-3.2.0-29-generic-pae              1
               =                initrd.img                                     3
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

Thanks in advance.

---

### Post by Mark Phelps on 2013-01-30
The info leads me to believe that you forced an installation onto an existing RAID system -- and the default installer does not understand RAID.

Sorry, not a RAID expert -- perhaps someone knowing more about RAID can tell you how to fix this.

---

### Post by ronparent on 2013-01-30
Your install is on /dev/mapper/isw_bhiddahgdf_ARRAY6? This being the case, it appears the boot loader should be on /dev/mapper/isw_bhiddahgdf_ARRAY. And that is where the Windows boot loader is (ie  => Windows is installed in the MBR of /dev/mapper/isw_bhiddahgdf_ARRAY).

You system is installed on what the Linux community refers to as a fakeRAID - a software RAID setup by Windows. You have to overwrite the Windows boot loader with a grub boot loader to boot to the install. Typically with the most recent releases of Ubuntu the boot loader does'n't automatically install properly. If you are willing to proceed, this is easily fixed.

Boot to a live cd session and open a terminal. Mount your install so -
> sudo mount /dev/mapper/isw_bhiddahgdf_ARRAY6 /mnt
You then install grub so -
> sudo grub-install --root-directory=/mnt/ /dev/dm-0
Paste and copy the above commands because they have to be entered exactly to work. That should get you in business! If you run into any problems, post here. Good luck.

---

### Post by oldfred on 2013-01-30
I do not know RAID either. But often we see this with Ultra-Books which regardless of computer brand use Intel configurations with RAID.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

            Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

