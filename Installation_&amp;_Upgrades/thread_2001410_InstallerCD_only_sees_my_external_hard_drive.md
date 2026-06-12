---
title: "InstallerCD only sees my external hard drive"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by Yankees1327 on 2012-06-10
I downloaded Ubuntu 12.04 x64 and burned the .iso to a DVD. When I boot from the DVD, it takes me to the installer but when I click on install, then it only shows my Western Digital MyBook which is a USB external hard drive that I only use for backups and do not intend to install Ubuntu on. I have two internal hard drives, neither of which it recognizes. One is a Seagate Barracuda 1TB which I have Windows 7 installed on, and the other is a Western Digital Caviar Blue 500GB on which I want to install Ubuntu. Both are sata 6.0gb/s, if that helps. 

Also, here is the data from the bootinfoscript I ran:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,953,458,175 1,953,456,128   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B640F12640F0EDCD                       ntfs       My Book
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


```
My system specs:
ASRock H61iCafe Motherboard
Intel i5 2400 @3.1 GHz Processor
8GB DDR3 Memory
XFX Radeon HD 6870 2GB Video Card
Ultra x4 600 Watt PSU
HT|Omega Claro Sound Card
The two hard drives I listed
and a regular HP DVD Writer which I am using to run  the installation CD.

Operating systems are Windows 7 Ultimate x64 and hopefully soon to be Ubuntu 12.04 x64.

---

### Post by darkod on 2012-06-11
Looks like they are not even detected. If you have SATA ports from two different controllers on the board, try connecting the disk(s) to different controller, or ports.

You can even try SATA 2 ports just to see if they will get recognized.

There is no setting like RAID or similar enabled in bios?

---

### Post by Mark Phelps on 2012-06-11
Some motherboards have the SATA ports divided so that some are 3 gb/s, others are 6 gb/s.  Try hooking up ONLY the drive that you want to install Ubuntu to, to the 3 gb/s SATA ports (all other hard drives disconnected) and see if the installer sees it then.

You may have to run Ubuntu at the slow data rate.

---

### Post by oldfred on 2012-06-11
If using a hard drive, there is no performance loss using SATA2. Only fast SSDs may need the advantages of SATA3.

[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
SATA revision 2.0 (SATA 3 Gbit/s)
SATA revision 3.0 (SATA 6 Gbit/s)
All SATA data cables meeting the SATA spec are rated for 3.0 Gbit/s and will handle current mechanical drives without any loss of sustained and burst data transfer performance. However, high-performance flash drives exceed the SATA 3 Gbit/s transfer rate; this is addressed with the SATA 6 Gbit/s interoperability standard.

---

### Post by Yankees1327 on 2012-06-11
Yep, changing to SATA2 made it recognize the hard drive. Thanks guys. Marking as solved.

---

