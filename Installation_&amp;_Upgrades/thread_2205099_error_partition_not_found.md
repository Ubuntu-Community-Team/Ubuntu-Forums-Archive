---
title: "error: partition not found"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by sachinharle2 on 2014-02-12
```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1         326,193,150   609,839,103   283,645,954   5 Extended
/dev/sda5         605,925,376   609,839,103     3,913,728  82 Linux swap / Solaris
/dev/sda2         609,839,104   625,121,279    15,282,176   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        BEC41A60C41A1B6B                       ntfs       HP_RECOVERY
/dev/sda5        03c0df20-aca5-4fa1-96a6-44c61b3ffbab   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)



```

---

### Post by Bucky Ball on 2014-02-12
Well, when is it giving that error? If you want help, you need to give a lot more information than this. 

For a start, you don't have Ubuntu installed, just grub. There is no EXT* partition so don't know what you've done ... or for that matter, what specifically you want to do.

Note this:

```
Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.
```

You have no partition 6 so you better explain how you got here. :-k

---

