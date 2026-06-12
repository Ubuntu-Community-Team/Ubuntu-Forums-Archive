---
title: "Yet another dual boot setup question"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by allanvv on 2011-03-03
I've installed Ubuntu onto a drive with Windows 7 installed already. Windows was set up using sda2 and sda3. I installed Ubuntu's /boot to sda1 and chose to install grub on sda1 instead of sda so it wouldn't overwrite Windows' bootloader.

However, now I can't boot into Windows, and the Grub menu screen doesn't have it show up. Should I have just let Grub install itself onto the MBR? Here's my bootinfo:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 22296 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800  83 Linux
/dev/sda2             206,848   409,602,047   409,395,200   7 HPFS/NTFS
/dev/sda3         409,602,048   716,802,047   307,200,000   7 HPFS/NTFS
/dev/sda4         716,804,094   798,832,639    82,028,546   5 Extended
/dev/sda5         716,804,096   794,927,103    78,123,008  83 Linux
/dev/sda6         794,929,152   798,832,639     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        a477574f-d396-499e-a6e2-4cf7bd4309b9   ext4                                     
/dev/sda2        D05A10975A107D02                       ntfs                                     
/dev/sda3        04D6733CD6732CD4                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e2586f86-5bd6-4f29-bd05-d1b65d4718f2   ext4                                     
/dev/sda6        67f1d4d9-6427-4313-ab60-9683448e8927   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)
/dev/sda1        /boot                    ext4       (rw,commit=0)


```

---

### Post by wilee-nilee on 2011-03-03
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

Your missing the highlighted part which was in sda1. Your also missing the bootflag on sda2 which needs to be put on with gparted before repairing. First boot a Ubuntu cd open gparted delete sda1 right click sda2 flags then click boot.

Then boot a W7 recovery cd and run the autorepiar to get the boot back in sometimes it needs to be run as many as three times. Here is a W7 recovery disc download if needed.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

So actually I think you will need to follow this link for purging and reinstalling grub as you have it shared between sda1 and sda5.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

