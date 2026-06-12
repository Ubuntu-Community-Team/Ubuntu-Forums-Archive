---
title: "Ubuntu on wubi does not boot"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by othip on 2012-03-27
I have ubuntu 11.10 installed with wubi which worked just fine for couple months. Then after several updates and sudden power-down accident(yes, it's my fault), ubuntu won't boot after grub menu and only black screen shows up with "Loading initial ramdisk" for recovery mode booting.

I have tried boot with nomodeset, no quiet splash, nosplash, accessing ubuntu fs from windows, boot recovery, checking disk, and trying to mount ubuntu fs from live usb. None worked.
I have Windows XP on Asus Eee, Ubuntu 11.10, grub 1.99.
I still have root.disk and swap.disk but grub.cfg and initrd.img are missing.
Grub sees the followings:
[PHP]grub>  ls
(memdisk)  (loop0)  (hd0)  (hd0,msdos3)  (hd0,msdos2)  (hd0,msdos1)[/PHP]And the following is the boot info script result:
[PHP]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:   Syslinux looks at sector 30456 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   302,246,909   302,246,847   7 NTFS / exFAT / HPFS
/dev/sda2         302,246,910   312,496,379    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7990 MB, 7990149120 bytes
256 heads, 30 sectors/track, 2032 cylinders, total 15605760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,360    15,605,759    15,603,400   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6C648DAC648D7A1A                       ntfs       
/dev/sda2        CCED-990E                              vfat       PE
/dev/sdb1        B1F2-1CF6                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /mnt/boot-sav/sda2       vfat       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
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

=============================== StdErr Messages: ===============================

umount: /mnt/boot-sav/sda1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
[/PHP]When I try to mount from live usb, I get the following:
[PHP]ubuntu@ubuntu:~$ sudo mkdir /mnt/windows /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/windows
ubuntu@ubuntu:~$ sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/temp
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail or so
ubuntu@ubuntu:~$ dmesg | tail
[  350.040636]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  350.040677]         06 18 1f bc 
[  350.040695] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  350.040718] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 06 18 1f b7 00 00 08 00
[  350.040756] end_request: I/O error, dev sda, sector 102244284
[  350.040819] ata3: EH complete
[  350.040932] Buffer I/O error on device loop1, logical block 3005503
[  350.040948] lost page write due to I/O error on loop1
[  350.391534] JBD: recovery failed
[  350.391546] EXT3-fs (loop1): error loading journal
[/PHP]Now I have no clue what's wrong and actually don't care anymore. As long as I can backup files, I am thinking of migrating to ubuntu in seperate partition. Does anybody have any idea how to? Thanks a lot.

---

### Post by darkod on 2012-03-27
Don't try to mount the disk. After you have mounted /dev/sda1 at /mnt/windows, try running fsck with something like:
sudo fsck /mnt/windows/ubuntu/disks/root.disk

I don't use wubi but I think it should work like that. In many cases fsck can repair corruption.

After that you try to see if it runs as normal, and if not you can try mounting it to try copying data.

---

### Post by othip on 2012-03-28
I can't believe it worked because I've also tried fsck couple times as well... Anyway, thank you so much!!! :D

---

### Post by othip on 2012-03-28
I  can't believe it worked because I've also tried fsck couple times as well... Anyway, thank you so much!!! :grin:

---

