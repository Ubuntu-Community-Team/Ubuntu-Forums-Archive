---
title: "Wubi Thinks it is Missing installation.iso"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by SeanFromIT on 2011-05-23
I didn't boot to Ubuntu for some months, when I did the other day it suddenly thought it needed to complete an installation and was missing installation.iso. So I uninstalled, downloaded the latest ubuntu desktop image and wubi, and re-installed. The fresh install is throwing the same installation.iso error. When I look, there is a C:\ubuntu\install\installation.iso. Why am I getting this error?

---

### Post by bcbc on 2011-05-23
I'm not sure, but I'd run chkdsk from windows and defragment (wubi relies on the host file system being clean) - plus if you can boot an Ubuntu live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") the results might help figure out what the problem is.

---

### Post by SeanFromIT on 2011-06-05
File system is clean, chkdsk found nothing. It looks like the "partition" wubi makes is not being seen. I tried installing off of a burned installation.iso and all I see are the NTFS partitions.

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   488,394,751   488,187,904   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

---

