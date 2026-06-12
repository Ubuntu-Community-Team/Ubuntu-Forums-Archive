---
title: "problem instalation using Wubi &quot;no root file system is defined&quot;"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by boumacmilan on 2013-08-03
Hi every Body

I have a lenovo Z570 with windows 8 on it and i want to install ubuntu 13.04 using Wubi the instalation on windows goes well but when i restart the PC to continue it gives me the error "[B]no root file system is defined"
[/B]
this is the result of the boot info script
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe /wubildr 
                       /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 2807616 of /dev/sdb1 for its 
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

/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             718,848   297,797,631   297,078,784   7 NTFS / exFAT / HPFS
/dev/sda3         297,797,632   717,228,031   419,430,400   7 NTFS / exFAT / HPFS
/dev/sda4         717,228,032   976,771,071   259,543,040   f W95 Extended (LBA)
/dev/sda5         717,230,080   976,769,023   259,538,944   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4051 MB, 4051697664 bytes
128 heads, 42 sectors/track, 1472 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,913,471     7,913,440   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       04529fbc-15bc-c341-9f76-1ca86e1155ec   ext2       
/dev/sda1        9E92CADB92CAB6D5                       ntfs       Réservé au système
/dev/sda2        BCD25BBBD25B791A                       ntfs       
/dev/sda3        6076C55576C52D1A                       ntfs       
/dev/sda5        4840CB4340CB368A                       ntfs       Ubuntu
/dev/sdb1        AE19-AA5B                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
  No volume groups found



```

thank you for you're helpe

---

### Post by TheFu on 2013-08-03
I was under the impression that WUBI didn't work with UEFI systems and wasn't supported after 12.04. I suppose I could be wrong.

[http://askubuntu.com/questions/254314/does-uefi-support-mean-wubi-will-now-work-on-laptops-shipped-with-windows-8](http://askubuntu.com/questions/254314/does-uefi-support-mean-wubi-will-now-work-on-laptops-shipped-with-windows-8) seems to backup my impression. Sorry.

Read up on the "Ubuntu UEFI howto" and get ready to dual boot. That seems to be the answer for now.

---

### Post by ajgreeny on 2013-08-03
> **TheFu said:**
> I was under the impression that WUBI didn't work with UEFI systems and wasn't supported after 12.04. I suppose I could be wrong.

[http://askubuntu.com/questions/254314/does-uefi-support-mean-wubi-will-now-work-on-laptops-shipped-with-windows-8](http://askubuntu.com/questions/254314/does-uefi-support-mean-wubi-will-now-work-on-laptops-shipped-with-windows-8) seems to backup my impression. Sorry.

Read up on the "Ubuntu UEFI howto" and get ready to dual boot. That seems to be the answer for now.

I am sure you are correct.  Not certain about the ubuntu version when it stopped working, but certainly it's a no-go on GPT and UEFI, so therefore will not work in Win8.

---

### Post by boumacmilan on 2013-08-03
Thanks for your answer
normaly it works (i instaled with Wubi on the onther Z570 with win8 and it woks fine) i don't now what's the problem with that one

---

### Post by bcbc on 2013-08-05
The problem is this:

```
Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             718,848   297,797,631   297,078,784   7 NTFS / exFAT / HPFS
/dev/sda3         297,797,632   717,228,031   419,430,400   7 NTFS / exFAT / HPFS
/dev/sda4         717,228,032   976,771,071   259,543,040   f W95 Extended (LBA)
/dev/sda5         717,230,080   976,769,023   259,538,944   7 NTFS / exFAT / HPFS


[COLOR=#ff0000]GUID Partition Table detected, but does not seem to be used[/COLOR].
```

The disk was previously used with a GUID partition table, and reusing as a MBR partitioned disk doesn't remove all the GPT data. When *ubiquity* (the ubuntu installer) runs, it uses *parted *to get the partition info, but *parted* will kick out an error in this case, which leaves *ubiquity* up the creek without a paddle.

You can use fixparts to clean it up - available here: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by grahammechanical on 2013-08-05
> [h=4]Windows installer is not compatible with Windows 8 or UEFI firmware, and is not available for Ubuntu 13.04.[/h]

From here
[URL="http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows"]
http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows[/URL]

Regards.

---

### Post by bcbc on 2013-08-05
> **grahammechanical said:**
> From here
[URL="http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows"]
http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows[/URL]

Regards.
They've changed the message. It's used to say that it wasn't compatible with computers with the Windows 8 sticker (i.e. pre-installed, i.e. using UEFI). 

Wubi works fine with Windows 8, just not with UEFI. In this case the computer is not booting with UEFI. Evidenced by the fact that *ubiquity* (i.e. Ubuntu) is running. So Wubi is in fact working.

PS they also released a working wubi.exe for 13.04, so again kind of misleading to say it's not available for 13.04. (It's easy enough for them to actually remove it rather than just saying it's not available).

---

### Post by boumacmilan on 2013-08-09
thanks all i tried the bcbc solution it work's fine

---

