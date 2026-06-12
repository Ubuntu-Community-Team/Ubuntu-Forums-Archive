---
title: "Can't Boot After New Install of 11.04"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by mrhayden on 2011-05-07
I tried to set up a dual boot system with win7.  I shrank my win7 partition by 75 gigs (it was taking up the entire HD), burned the 11.04 64bit to a CD, and restarted.  The CD booted fine and I chose "install alongside windows", and the install seemed to go fine. After prompting for a restart, I get a black screen with an error message that changes every restart (usually a string of numbers/letters that it says does not exist), followed by a command prompt.  I can't boot into either Linux or Windows, right now I'm just using the cd.  I have 2 harddrives in RAID 0 format, but I'm not sure if that's an issue.   

i found the boot info script in another thread and ran it.  Seems like a lot of unknowns/errors?

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for cdh.
 => Grub 2 is installed in the MBR of /dev/mapper/isw_cgiifagaha_Volume0 and 
    looks on the same drive in partition #5 for cdh.

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

isw_cgiifagaha_Volume01: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cgiifagaha_Volume02: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2             411,648 1,799,933,951 1,799,522,304   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: isw_cgiifagaha_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_cgiifagaha_Volume0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_cgiifagaha_Volume01   *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/mapper/isw_cgiifagaha_Volume02            411,648 1,799,933,951 1,799,522,304   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_cgiifagaha_Volume0p1 C252B81B52B8165F                       ntfs       System                        
/dev/mapper/isw_cgiifagaha_Volume0p2 E6B4BA0FB4B9E1EB                       ntfs       Windows                       
/dev/mapper/isw_cgiifagaha_Volume0: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
error: /dev/mapper/isw_cgiifagaha_Volume01: No such file or directory
error: /dev/mapper/isw_cgiifagaha_Volume02: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_cgiifagaha_Volume0
isw_cgiifagaha_Volume0p1
isw_cgiifagaha_Volume0p2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/dm-1        /media/System            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on isw_cgiifagaha_Volume01


Unknown BootLoader  on isw_cgiifagaha_Volume02



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/mapper/isw_cgiifagaha_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cgiifagaha_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cgiifagaha_Volume02: No such file or directory
hexdump: /dev/mapper/isw_cgiifagaha_Volume02: No such file or directory
```

---

