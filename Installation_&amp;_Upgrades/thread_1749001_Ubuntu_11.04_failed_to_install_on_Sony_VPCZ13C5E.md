---
title: "Ubuntu 11.04 failed to install on Sony VPCZ13C5E"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by crgal on 2011-05-04
I may have incompatible hardware here but the install seemed to get right to the end and then failed with the following error :-

Unable to install Grub in /dev/sda
Executing Grub-Install /dev/sda failed
This is a Fatal error

Live CD is able to read read the new filesytem on the raid volume (with 4 x 128GB disks). 
Disk Utility and GParted seem to read the raid array OK but I am out of my depth in knowing how to fix this problem if it can be fixed!

The result.txt from boot_info_script is shown below :-

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/mapper/isw_dijbjabefg_Volume0

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dijbjabefg_Volume01: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dijbjabefg_Volume02: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dijbjabefg_Volume03: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dijbjabefg_Volume04: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_dijbjabefg_Volume05: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dijbjabefg_Volume06: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dijbjabefg_Volume07: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dijbjabefg_Volume08: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    16,654,335    16,652,288  27 Hidden HPFS/NTFS
/dev/sda2          16,654,336    16,859,135       204,800   7 HPFS/NTFS
/dev/sda3    *     16,859,136   510,889,983   494,030,848   7 HPFS/NTFS
/dev/sda4         510,892,030 1,000,257,535   489,365,506   f W95 Ext d (LBA)
Invalid MBR Signature found
/dev/sda5     ?   510,892,030   510,892,029                   Unknown
/dev/sda6     ?   510,892,030   510,892,029                   Unknown

/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda4
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda4

Drive: isw_dijbjabefg_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_dijbjabefg_Volume0: 512.1 GB, 512133431296 bytes
255 heads, 63 sectors/track, 62263 cylinders, total 1000260608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dijbjabefg_Volume01              2,048    16,654,335    16,652,288  27 Hidden HPFS/NTFS
/dev/mapper/isw_dijbjabefg_Volume02         16,654,336    16,859,135       204,800   7 HPFS/NTFS
/dev/mapper/isw_dijbjabefg_Volume03   *     16,859,136   510,889,983   494,030,848   7 HPFS/NTFS
/dev/mapper/isw_dijbjabefg_Volume04        510,892,030 1,000,257,535   489,365,506   f W95 Ext d (LBA)
/dev/mapper/isw_dijbjabefg_Volume05        510,892,032   715,692,031   204,800,000   7 HPFS/NTFS
/dev/mapper/isw_dijbjabefg_Volume06        981,936,128 1,000,257,535    18,321,408  82 Linux swap / Solaris
/dev/mapper/isw_dijbjabefg_Volume07        715,693,056   965,824,511   250,131,456  83 Linux
/dev/mapper/isw_dijbjabefg_Volume08        965,825,536   981,924,863    16,099,328  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dijbjabefg_Volume0p1 E21EBF511EBF1E0B                       ntfs       Recovery                      
/dev/mapper/isw_dijbjabefg_Volume0p2 ECF8D414F8D3DB42                       ntfs       System Reserved               
/dev/mapper/isw_dijbjabefg_Volume0p3 1C50D4C850D4AA32                       ntfs                                     
/dev/mapper/isw_dijbjabefg_Volume0p5 DAC84090C8406D37                       ntfs       Data                          
/dev/mapper/isw_dijbjabefg_Volume0p6 f7db0f8d-63e6-48ae-a906-dd9c2d99c294   swap                                     
/dev/mapper/isw_dijbjabefg_Volume0p7 85fd100a-0f97-4c5b-8115-e556282ff15f   ext4                                     
/dev/mapper/isw_dijbjabefg_Volume0p8 2f42c355-bed2-4a7d-92e9-afcfb8b6846c   swap                                     
/dev/mapper/isw_dijbjabefg_Volume0: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc                                                isw_raid_member                               
/dev/sdd                                                isw_raid_member                               
error: /dev/mapper/isw_dijbjabefg_Volume01: No such file or directory
error: /dev/mapper/isw_dijbjabefg_Volume02: No such file or directory
error: /dev/mapper/isw_dijbjabefg_Volume03: No such file or directory
error: /dev/mapper/isw_dijbjabefg_Volume04: No such file or directory
error: /dev/mapper/isw_dijbjabefg_Volume05: No such file or directory
error: /dev/mapper/isw_dijbjabefg_Volume06: No such file or directory
error: /dev/mapper/isw_dijbjabefg_Volume07: No such file or directory
error: /dev/mapper/isw_dijbjabefg_Volume08: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dijbjabefg_Volume0
isw_dijbjabefg_Volume0p1
isw_dijbjabefg_Volume0p2
isw_dijbjabefg_Volume0p3
isw_dijbjabefg_Volume0p5
isw_dijbjabefg_Volume0p6
isw_dijbjabefg_Volume0p7
isw_dijbjabefg_Volume0p8

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/dm-6        /media/1C50D4C850D4AA32  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on isw_dijbjabefg_Volume01


Unknown BootLoader  on isw_dijbjabefg_Volume02


Unknown BootLoader  on isw_dijbjabefg_Volume03


Unknown BootLoader  on isw_dijbjabefg_Volume04


Unknown BootLoader  on isw_dijbjabefg_Volume05


Unknown BootLoader  on isw_dijbjabefg_Volume06


Unknown BootLoader  on isw_dijbjabefg_Volume07


Unknown BootLoader  on isw_dijbjabefg_Volume08



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume01: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume01: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume02: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume02: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume03: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume03: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume04: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume04: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume05: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume05: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume06: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume06: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume07: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume07: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume08: No such file or directory
hexdump: /dev/mapper/isw_dijbjabefg_Volume08: No such file or directory

```If anyone can help me with this problem I would be very grateful.

---

### Post by crgal on 2011-09-10
I have finally solved this problem with help from the folks at [www.adhocism.net](www.adhocism.net) 

My Sony VPCZ13C5E laptop will now dual boot into Windows 7 or Ubuntu 11.04. However I must say booting now takes quite a while
 with a worryingly long black screen just before the Ubuntu login appears.

There are a number of issues with its operation in Ubuntu such as the speed stamina switch does not work and I think sleep/hibernate and power control has problems but at least I have a usable system. :)

Solutions to these problems are also described at the following address :-

[http://www.adhocism.net/2011/05/installing-ubuntu-11-04-on-sony-vaio-vpc-z13m9eb/](http://www.adhocism.net/2011/05/installing-ubuntu-11-04-on-sony-vaio-vpc-z13m9eb/)
but I have not tried them yet - I have been so relieved to get something working.

I used the 64 bit Alternate Install iso burnt to CD and followed the instructions at the above address. Remember to set the GPU switch to stamina!

Hope this helps others with the same problem.

Many thanks to the people at adhocism.

---

### Post by crgal on 2011-11-13
I upgraded to Ubuntu 11.10 in the hope that the boot time would improve. However that was not the case and I had a number of issues particularly relating to the speed - stamina switch.

The solution was a complete reinstall using the 11.10 alternate AMD64.iso (with the speed switch set to stamina and saying yes to install the raid setup) which I must say has solved most of the common issues I had been having. It still takes about 15 seconds to the boot menu and then 15 more to the Light Display Manager logon screen. Also it boots OK back into Win 7.

Most things work including the SD slot, but I still cannot get the internal sim card to be recognised, however my vodafone sim works in my O2 dongle!

Many thanks to all those guys who put in all the development to get this sorted in the latest issue of Ubuntu.

---

