---
title: "booting problem"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by stefan3178 on 2012-01-28
Hi.
I have a problem.
I have a 250 gb hard disk no1 (Windows xp installed, bootable) and an other 250 gb hard disk no2. I make a bootable usb flash disk with ubuntu 11.10 kit. I made manual partitioning on hard disk no2 (200 mb for /boot as primary, 4 gb swap logical, the rest of space for /). the installation went ok. 
I restarted the computer and it detects both hard drives and immediately freezes and doesn't want to boot (from no1 or no2 or usb). I also cannot enter in BIOS.
I can access the bios or boot from hard disk no1 or from usb flash disk only when hard disk no2 is removed from the computer. Otherwise the computer doesn't boot or cannot enter in bios.
What could be the problem? failed bootloader? how can i repair the problem?
I also removed and put back the bios battery, restore the bios to factory settings, changed/swithched the cables, verified jumpers and then connect back the hard drive no2 but the same problem. Connecting only hard drive no2 without hard no1, cd-rom or usb flash disk gives the same problem. 
Any idea?

---

### Post by ajgreeny on 2012-01-28
I suspected that you may have put grub onto the mbr of disk 1, but the config files for grub are on the second disk, in the boot partition, which incidentally is an unnecessary complication.  You can, however, boot from the first disk without problem, so that can not be the reason.  I wonder if the second disk is causing the BIOS to lock for some reason, even though it is detected.

To get a full picture it would have been useful for you to run your USB live system with the second disk attached, click on the Boot-Info-Script link in my signature and follow the instruction there.  However, you say you can not go to the BIOS, nor boot the usb if the second disk is attached, which seems odd, as the BIOS runs before anything of the bootloader files is read.  It may still be worth trying the script I mentioned using the USB live system, even with the second disk removed, but it will probably not help a great deal.

Do you go straight to windows with no problem if the second disk is removed?

---

### Post by stefan3178 on 2012-01-28
Possibly could be an mbr problem as you say. I will try the script. The second disk causes the booting problem. Yes it's strange that it freezes the booting without giving an error message and doesn't let me enter into BIOS even if I press the Del (which usually works) before the checking of the RAM memory starts. Touching the hard drive I feel it works. After the RAM memory test finishes, the computer detects successfully the mouse, keyboard, CD-ROM drive, both hard drives, then freezes. If I remove the hard drive no2 from the computer then all works fine.

---

### Post by stefan3178 on 2012-01-28
The results of the Boot-info-script script are the following (during this test the hard drive no2 was removed from the computer; I also have 2 linux versions installed as windows apps via wubi):


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 15400 of /dev/sdb for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9A70BD2C70BD104D                       ntfs           windows XP
/dev/sdb         1F05-0464                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr="Ubuntu"
C:\jolildr.mbr="Joli OS"

---

### Post by dino99 on 2012-01-28
might help:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by stefan3178 on 2012-01-28
Thanks but my problem is not related with wubi which is on hard drive no1. The problem is with hard drive no2 which has ubuntu installed on linux partitions.

---

### Post by stefan3178 on 2012-01-28
I put hard drive no2 as primary master, i removed cd rom drive, hard drive no1 from the computer, the same booting problem appears. The keyboard is not frozen CTRL+alt+del is working, on the screen I read the last message:
Primary Master hard drive detected:
WDC WD2500JB-22REA0 20.00K20
Ultra DMA MODE-3 SMART Capable and Status OK.

Still doesnt boot.

---

