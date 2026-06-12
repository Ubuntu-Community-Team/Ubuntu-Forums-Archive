---
title: "Trying to dual boot Ubuntu and Windows 7, Win7 installed first"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by dismas on 2010-09-24
Hi, I'm trying to dual boot Ubuntu and Win7, with Win7 installed first. I shrunk my Win7 partition to get 100 GB free space. However, I am unable to select that partition when trying to install Ubuntu. This is a laptop. The current partitions are Windows 7, the empty partition, and two HP partitions (for recovery or something). Why can't I install Ubuntu to the 104857 MB partition? Thanks for your time.


[IMG]http://i.imgur.com/tADng.png[/IMG]

[IMG]http://i.imgur.com/It1M5.png[/IMG]

---

### Post by aytech on 2010-09-24
Create a separate partition with Gparted. then you should have the option "Use the largest available free space".

---

### Post by Rubi1200 on 2010-09-24
According to the second screenshot you already have 4 primary partitions which is the maximum allowable. That is why you are unable to install to the space you created.

This is my suggestion:
Use the LiveCD and post the results of the bootscript linked to at the bottom of my post, then we can advise you further.

---

### Post by dismas on 2010-09-24
RESULTS.txt:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

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

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   727,175,167   726,765,568   7 HPFS/NTFS
/dev/sda3         931,975,168   976,560,127    44,584,960   7 HPFS/NTFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,646,719    15,638,656   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0E2CEA222CEA0515                       ntfs       SYSTEM                        
/dev/sda2        026EFFF36EFFDD7B                       ntfs                                     
/dev/sda3        68B2CE20B2CDF31C                       ntfs       RECOVERY                      
/dev/sda4        DCD8-07D2                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14D5-D83A                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

