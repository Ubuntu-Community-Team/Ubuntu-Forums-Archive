---
title: "I gave up on RAID0 and ..."
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by divxclub on 2011-02-11
Hi guys after several unsuccessful tried to install Ubuntu on RAID0 alongside with Windows 7 I just deleted whole array and now I got just 2 separate SDDs ... I already installed Windows on one and formatted second one to have about 20gb of unallocated space for ubuntu. Just want to show you live cd results.txt if you see anything that may give me troubles.

Thanks !


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/mapper/isw_dfajjchfee_RAID0

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 324. But according to the info from fdisk, 
                       sdb5 starts at sector 1948299264.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_dfajjchfee_RAID01: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dfajjchfee_RAID02: _________________________________________________________________________

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

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    92,653,567    92,446,720   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,948,298,939 1,948,296,892   7 HPFS/NTFS
/dev/sdb2       1,948,298,940 1,953,520,064     5,221,125   5 Extended
/dev/sdb5       1,948,299,264 1,953,517,567     5,218,304   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
256 heads, 63 sectors/track, 90845 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdc1 ends after the last sector of /dev/sdc

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34       262,177       262,144 Microsoft Windows
/dev/sdc2         264,192 1,174,204,415 1,173,940,224 Linux or Data

Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               2,048    61,933,567    61,931,520   7 HPFS/NTFS


Drive: isw_dfajjchfee_RAID0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_dfajjchfee_RAID0: 2250.5 GB, 2250461675520 bytes
256 heads, 63 sectors/track, 272534 cylinders, total 4395432960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dfajjchfee_RAID01                  1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/mapper/isw_dfajjchfee_RAID01             34       262,177       262,144 Microsoft Windows
/dev/mapper/isw_dfajjchfee_RAID02        264,192 1,174,204,415 1,173,940,224 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dfajjchfee_RAID0: PTTYPE="gpt" 
/dev/sda1        80BAF84CBAF83FE8                       ntfs       System Reserved               
/dev/sda2        3E0036100035D01F                       ntfs       OS SSD                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        26C0F80EC0F7E1CB                       ntfs       WD                            
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        E60EEC0B0EEBD31B                       ntfs       WD2                           
/dev/sdb: PTTYPE="dos" 
/dev/sdc                                                isw_raid_member                               
/dev/sde                                                isw_raid_member                               
/dev/sdf1        B60EFDC30EFD7D25                       ntfs       Software SSD                  
/dev/sdf: PTTYPE="dos" 
/dev/sdg                                                isw_raid_member                               
error: /dev/mapper/isw_dfajjchfee_RAID01: No such file or directory
error: /dev/mapper/isw_dfajjchfee_RAID02: No such file or directory
error: /dev/sdc1: No such file or directory
error: /dev/sdc2: No such file or directory
error: /dev/sdd: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dfajjchfee_RAID0

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2


Unknown BootLoader  on isw_dfajjchfee_RAID01


Unknown BootLoader  on isw_dfajjchfee_RAID02



=======Devices which don't seem to have a corresponding hard drive==============

sdd 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/mapper/isw_dfajjchfee_RAID01: No such file or directory
hexdump: /dev/mapper/isw_dfajjchfee_RAID01: No such file or directory
hexdump: /dev/mapper/isw_dfajjchfee_RAID02: No such file or directory
hexdump: /dev/mapper/isw_dfajjchfee_RAID02: No such file or directory

---

