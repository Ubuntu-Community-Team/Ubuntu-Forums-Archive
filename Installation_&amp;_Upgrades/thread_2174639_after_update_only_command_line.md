---
title: "after update only command line"
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by Luigi_Corvino on 2013-09-15
after updating only command line with grub, something like this without graphic user interface

 Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.
I did what MacBook Pro 10,1 retina suggest in this post [http://ubuntuforums.org/showthread.php?t=1807508](http://ubuntuforums.org/showthread.php?t=1807508)



```
       Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     31,459,328    31,664,127       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          31,664,128   976,771,071   945,106,944   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DE06374606371EC9                       ntfs       PQSERVICE
/dev/sda2        6AE437B3E437807D                       ntfs       SYSTEM RESERVED
/dev/sda3        84D638CBD638BF6C                       ntfs       Acer
/dev/sr0                                                iso9660    Ubuntu 12.04.3 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3/Wubi




```

---

### Post by hakuna_matata on 2013-09-15
> **Luigi_Corvino said:**
> 
```

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk


```
Missing /ubuntu/disks/root.disk.... Try [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

### Post by Luigi_Corvino on 2013-09-15
Thank you but it doesn't work, he can't find and recognize the found.000 . Any other solutions please? it is really important! Thank you in advance for your help!

---

### Post by Quackers on 2013-09-15
Did you mean me?  :D
The thread you quoted was for a dual boot system and your wubi installation is quite different. Sadly I know nothing about wubi installs.
I suggest you look at the wubi megathread and see if your problem has been seen before.

[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by hakuna_matata on 2013-09-16
> **Luigi_Corvino said:**
> Thank you but it doesn't work, he can't find and recognize the found.000
Wubi needs a file called root.disk in your Windows file system. No file = Ubuntu inside Windows doesn't work. Maybe tools like photorec can help. [http://en.wikipedia.org/wiki/PhotoRec](http://en.wikipedia.org/wiki/PhotoRec)

---

