---
title: "LiveCD install issues/No hard drives = no install"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by RheaHS on 2011-05-31
Ended up with major problems last night, after a really messed up upgrade and a power cut, now nothing will boot. 
I used the Live USB to see if I could check for faults, or at the worst format and reinstall, but my Hard Drives are being seen but not mounting (getting various errors for this from (Daemon is inhibited) to Busy. 
That I've been looking around here for answers for, but still can't solve what is happening. 

My drives are seen in BIOS, Disk Utility, etc. , but when I try to mount, it seems to work but none of the three can be accessed, the Daemon errors come then. All disks show as healthy, except one with a bad sector. I can't fix that either right now. 

When I try to run gparted or the install program, it freezes, and won't go past searching for drives. 

Here are the results from Boot Script
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 2048.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......S..:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 3328 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   312,576,704   312,576,642   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   231,071,743   231,069,696  83 Linux
/dev/sdb2         231,073,790   234,440,703     3,366,914   5 Extended
/dev/sdb5         231,073,792   234,440,703     3,366,912  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2006 MB, 2006974464 bytes
16 heads, 32 sectors/track, 7656 cylinders, total 3919872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          8,064     3,919,871     3,911,808   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6853-5BA9                              vfat       LaCie
/dev/sdb1        15AD-B6A6                              vfat       120GB HDD
/dev/sdb5        1748cf3d-124c-4aa0-b591-96ea3d102c02   swap       
/dev/sdc1        a237f411-43d8-4739-a161-2dac5757d3c3   ext4       
/dev/sdc5        f72a56de-fd17-4b90-a09b-d62a1bb1be04   swap       
/dev/sdd1        FEE3-850A                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

I can post any other information that is needed, it was all working fine before this hiccup, had it all recognised.

---

### Post by Rubi1200 on 2011-05-31
Hi,
my first suggestion would be to try and run an fsck from the LiveCD on sdb.

If that doesn't work, download and run as a LiveCD Slax. I have seen people use it when other live distros were having troubles doing the same thing:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

---

### Post by RheaHS on 2011-05-31
I don't have a CD drive/DVD drive atm, so this could be interesting, also running out of USB drives. 

I'm running the fsck now, it seems I can now mount two of the drives, so getting there. Any other ideas are welcome

---

### Post by RheaHS on 2011-05-31
Output from fsck ```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/sdc
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

uh oh...


UPDATE...somehow managed to format the disc to ext2, but the install is still freezing.

---

### Post by Rubi1200 on 2011-05-31
My suggestion is that you try and find a way to access your data if possible and save it before continuing.

Then, try the commands to use the backup superblocks.

More information here:
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

---

### Post by RheaHS on 2011-05-31
It's showing as a clean, new filesystem now, but the install program is still freezing when searching for disks. All HDDs show in Disk Utility and Gparted now, and I can mount them, but when it comes to installing, no joy.

---

### Post by Rubi1200 on 2011-06-01
You may want to consider using the Alternate CD to try and install.

But, you may also want to check things like memory and hard disk integrity as far as these issues are concerned.

---

### Post by RheaHS on 2011-06-01
All discs test fine in the utility, so its strange. As for the alternate install disc, no working optical drives atm.

---

