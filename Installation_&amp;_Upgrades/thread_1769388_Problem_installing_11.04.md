---
title: "Problem installing 11.04"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by Phagocyte on 2011-05-27
When I try to install Ubuntu 11.04 ( Not using WUBI ).. My already present OS Windows 7 is not being detected. More over I get two options, 

1)Erase the disk and install
2)Specify the partitions

When I try to specify the partitions, my hard disk is shown.. but my 4 partitions are not visible.

Please help me out.

---

### Post by Hedgehog1 on 2011-05-28
We need to get a look at your PC to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by Phagocyte on 2011-06-03
Posting after doing what you've said

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   122,881,184   122,881,122   7 NTFS / exFAT / HPFS
/dev/sda2         122,881,248   286,721,975   163,840,728   7 NTFS / exFAT / HPFS
/dev/sda3         286,728,183   558,000,846   271,272,664   7 NTFS / exFAT / HPFS
/dev/sda4         558,001,710   625,153,409    67,151,700   f W95 Extended (LBA)
/dev/sda5         558,002,176   625,139,711    67,137,536   7 NTFS / exFAT / HPFS

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,625,215    15,625,184   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        246C9E756C9E420A                       ntfs       
/dev/sda2        E286BCE686BCBBFB                       ntfs       Acads
/dev/sda3        006CD3DE6CD3CC92                       ntfs       Media
/dev/sda5        647CD6237CD5F032                       ntfs       
/dev/sdb1        6218-6E6E                              vfat       TEJA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")


---

### Post by Phagocyte on 2011-06-03
I had some network problems and could not access internet. Please solve this problem. I really want to explore ubuntu.. Thanks

---

### Post by Phagocyte on 2011-06-03
[[IMG]http://img8.imageshack.us/img8/2999/screenshotegg.png[/IMG]]("http://img8.imageshack.us/i/screenshotegg.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

This is how it looks..

---

### Post by Phagocyte on 2011-06-03
Please respond!! Please.. :(

---

### Post by Phagocyte on 2011-06-03
Help me outtt!!! Echoooo!!! :(

---

### Post by Phagocyte on 2011-06-04
Please respondd!! :(

---

### Post by Phagocyte on 2011-06-04
I give up! :(

---

### Post by mörgæs on 2011-06-04
> **Phagocyte said:**
> I give up!

Thanks. As you can see, bumping is not welcome and does not increase your chances of getting an answer.

---

### Post by Phagocyte on 2011-06-04
Im sorry. Was a bit frustrated..

---

