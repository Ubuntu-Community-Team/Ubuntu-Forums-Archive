---
title: "Need help with failed install- my fault"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by neubert500 on 2010-10-12
I attempted to dual boot win 7 and ubuntu. I messed up somehow and attempted to redo the install. Yep you guessed it, I hosed it and now cannot get the system to boot in either OS. I have tried twice to used the recovery disks for win 7 but get the grub error.
Here is the result of boot info script:

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    27,650,047    27,648,000  27 Hidden HPFS/NTFS
/dev/sda2    *     27,650,048    27,854,847       204,800   7 HPFS/NTFS
/dev/sda3          27,854,848   122,307,418    94,452,571   7 HPFS/NTFS
/dev/sda4         122,308,606   488,396,799   366,088,194   5 Extended
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        7AECE70BECE6C10D                       ntfs       SYSTEM RESERVED               
/dev/sda3        A052DA4952DA23B6                       ntfs       ACER                          
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

Any and all help would be gratefully accepted.


Thanks for all the help, I solved the issue. If anyone else is thinking about dual booting win7 and Ubuntu, make a win7 rescue disk first and learn the dos command to rebuild your mbr
Thank you.

---

