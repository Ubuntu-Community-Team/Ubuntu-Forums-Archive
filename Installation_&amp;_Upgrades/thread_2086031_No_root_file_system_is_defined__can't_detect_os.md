---
title: "No root file system is defined / can't detect os"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by iSetsuna on 2012-11-19
As with what the title says, when i install ubuntu using wubi an error pops out saying "NO ROOT FILE SYSTEM IS DEFINED, PLEASE CORRECT THIS FROM THE PARTITIONING MENU. When using LIVE USB, my OS is not detected. I already reviewed similar threads but starting a new one would be a better idea just in case the solution is a bit different.

So heres my bootscript output.
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 60154 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   747,522,047   747,520,000   7 NTFS / exFAT / HPFS
/dev/sda2         747,522,048   976,771,071   229,249,024   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sdb2             718,848    46,901,247    46,182,400   6 FAT16


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 7914 MB, 7914651648 bytes
122 heads, 58 sectors/track, 2184 cylinders, total 15458304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064    15,458,303    15,450,240   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A6ECED85ECED4FDB                       ntfs       
/dev/sda2        EC3C59383C58FF50                       ntfs       
/dev/sdb1        7CC6433CC642F5C4                       ntfs       System Reserved
/dev/sdc1        0CED-1D6E                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
  No volume groups found
```

---

### Post by darkod on 2012-11-19
You see in the partitions results where is says 'guid partition table detected but doesn't seem to be used'?

You had gpt tables on both disks and used windows to make new msdos tables. But windows doesn't delete the backup gpt table which linux can detect and it gets confused.

Use the ubuntu cd in live mode (Try Ubuntu), install fixparts from the .deb they have on their website, and then use it to remove the gpt remains. It's enough to open the disk with fixparts and it will offer to remove it, like:
sudo fixparts /dev/sda

Fixparts website: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

On another note, I would consider a proper ubuntu installation instead of wubi inside windows. The OS is designed to work by itself, not as virtual in windows.

---

