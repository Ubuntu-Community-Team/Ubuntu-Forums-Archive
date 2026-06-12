---
title: "Trying to boot WinVista; Getting Grub Resuce Screen"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by Plastic_Cow on 2010-08-25
I recently installed Ubuntu onto my laptop. However, in the process my Windows Vista was overwritten. I tried reinstalling Windows with the recovery discs, however, ever time I restart I get the same message "No Partition found" then it load Rescue Grub. I've tried loading up the live disc and removing grub, but afterwards the same message shows up. Hope you guys have a better idea than I do on this.

---

### Post by Rubi1200 on 2010-08-25
Hi,
boot the computer with the Ubuntu CD.
Post the results of the bootscript linked to at the bottom of my post.

---

### Post by Plastic_Cow on 2010-08-25
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    24,579,449    24,579,387   c W95 FAT32 (LBA)
/dev/sda2          24,580,096   976,771,071   952,190,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D476-EF15                              vfat       RECOVERY                      
/dev/sda2        8C0ADCE00ADCC87A                       ntfs       Vista64                       
/dev/sda: PTTYPE="dos" 
/dev/sdb         5608-1CAA                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/DRIVER_CD_VISTA_30 udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077)

---

### Post by Rubi1200 on 2010-08-25
Do you have the Vista installation CD or just a recovery disk?

EDIT:
these are the instructions to restore the Vista bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Scroll down to the relevant section.

---

### Post by Plastic_Cow on 2010-08-25
Just the recovery disc.

---

### Post by Rubi1200 on 2010-08-25
> **Plastic_Cow said:**
> Just the recovery disc.
See my previous post for instructions on how to restore the Vista bootloader. 

It appears as if Ubuntu is no longer there, but GRUB still thinks it is.

The fix should get you back into Vista and then you can, hopefully, reinstall Ubuntu.

Let me know if you have any questions.

---

