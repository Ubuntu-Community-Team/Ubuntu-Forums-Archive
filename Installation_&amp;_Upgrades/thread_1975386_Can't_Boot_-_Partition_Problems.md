---
title: "Can't Boot - Partition Problems"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by ube17 on 2012-05-07
i have same problem, i use windows xp home and ubuntu netbook remix

[B]GRUB loading.
Welcome to GRUB!

error: no such partition.
Entering rescue mode...
grub rescue>[/B] 

this is my bootinfoscript
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1912888 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys 
                       /syslinux/ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x233b233a

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    10,236,050    10,235,988  12 Compaq diagnostics
/dev/sda2     ?    10,236,051    94,124,834    83,888,784   7 NTFS / exFAT / HPFS
/dev/sda3          94,124,835    96,116,894     1,992,060  82 Linux swap / Solaris
/dev/sda4          96,117,019   312,578,594   216,461,576   f W95 Extended (LBA)
/dev/sda5         136,065,321   186,749,387    50,684,067   7 NTFS / exFAT / HPFS
/dev/sda6         186,749,451   312,578,594   125,829,144   7 NTFS / exFAT / HPFS
/dev/sda7          96,117,021   136,054,484    39,937,464  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4018 MB, 4018143232 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1714ece2

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,847,935     7,847,873   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        5430-7D5C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/sr0         /media/XP SP2            iso9660    (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default /syslinux/menu.c32
prompt 0
timeout 300
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys
            ?? = ??             syslinux/ldlinux.sys
            ?? = ??             syslinux/menu.c32
            ?? = ??             syslinux/syslinux.cfg
            ?? = ??             syslinux/vesamenu.c32

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4


Unknown BootLoader on sda5


Unknown BootLoader on sda6


Unknown BootLoader on sda7



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```there is no such file or directory, open gparted, partition is unalocated
[IMG]http://cdn-u.kaskus.us/72/whky7ypm.png[/IMG]

but if i open with mini xp on hirens boot cd, my partition is normal
[IMG]http://cdn-u.kaskus.us/72/8lqw98hg.jpg[/IMG]

when i try this command ```
sudo mount /dev/sda7 /mnt
``` and not working
[IMG]http://cdn-u.kaskus.us/72/ajsxzbeu.png[/IMG]

and then, i use live usb ubuntu remix 9.04 and try this [How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 11.10)]("http://ubuntuforums.org/showthread.php?t=1014708") not working
i try [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") but packages are available on ubuntu 10.04 or later
and try [grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") is not available

thanks for your help :)

---

### Post by oldfred on 2012-05-07
I have seen script not mount a partition where for NTFS chkdsk was required or for ext type partitions e2fsck was needed, but not mounting all the partitions? And partition table still looks ok other than a ? in the boot flag is not normal. That may be enough to cause bigger problems or something else is wrong.

First lets backup partition table.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

What does testdisk show? It may show everything is normal if partition table is ok.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

From a Windows disk can you run chkdsk on your NTFS partition. 

And try this on your sda7 partition from your liveCD.
#From liveCD so everything is unmounted,swap off if necessary, change example shown with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda7
#if errors:
sudo e2fsck -f -y -v /dev/sda7

---

