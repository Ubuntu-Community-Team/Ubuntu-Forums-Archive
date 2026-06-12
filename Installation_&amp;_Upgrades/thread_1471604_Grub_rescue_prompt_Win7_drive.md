---
title: "Grub rescue prompt Win7 drive"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Wilson423 on 2010-05-03
After installing 10.04 on a second drive and it messed up my primary drive running Windows 7. Booting my primary drive brings me to the grub rescue prompt while the secondary drive does not boot at all.

The Process (as I remember): I booted from a jump drive, formatted secondary drive, installed U 10.04, everything got buggered.

At the suggestion of a previous thread, I started this thread and posting the bootinfoscript as suggested. NOTE: the secondary drive is not attached to the computer at the time of this boot info run.

I have tried the Win7 recovery CD and it has failed with boot recovery, system restore, and it cannot see the HP Factory Image on that drive. The restore feature after POST does not work. 

Any help would be appreciated.

Thanks




                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,930,930,175 1,930,723,328   7 HPFS/NTFS
/dev/sda4       1,930,930,176 1,953,521,663    22,591,488   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5E90506890504923                       ntfs       SYSTEM                        
/dev/sda2        2C3C57F33C57B694                       ntfs       HP                            
/dev/sda4        B0441E25441DEEBA                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        81E3-F491                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda2        /media/HP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/FACTORY_IMAGE     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by Wilson423 on 2010-05-03
Fixed!!
All Hail SINternet!!

>>Had the same thing but after my first attempt I just had a blinking cursor when I selected Win 7. Ubuntu booted just fine.

I selected all devices for Grub.

I then (with the Windows 7 DVD) booted and started the repair.
Selected Command prompt after a failed automatic repair.

Type the following;
bootrec /fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd

This should get you back your Win 7.

Now. I then attempted another 9.10 install. Upgraded and this time only selected the Ubuntu partition. I ended up with the grub recovery prompt.

I recovered my Win 7 and will install 9.10 but WILL NOT UPGRADE.<<

---

