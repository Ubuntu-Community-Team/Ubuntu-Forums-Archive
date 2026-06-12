---
title: "Ubuntu 11.04 Install Snag"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by xx1ndy500xx on 2011-05-24
Okay here's my deal. I have a Compaq Presario CQ56 109-WM laptop.
It has a Celeron 900 (64bit) processor and an Intel 4 series graphics card in it. I'm not sure which one specifically. I currently have windows 7 installed. Which is very fresh. I had just installed it the day before attempting the Ubuntu install. I downloaded the 64bit version of Ubuntu 11.04 from Ubuntu's website. Burnt it to a cd-r and attempted to install it on my laptop. It will boot just fine into the installation setup. I choose my language and click "Install Ubuntu". The installation goes to the preparing to install Ubuntu page with the check list. Everything looks fine. (I tried downloading updates while installing and not.) I click forward and nothing happens. The little mouse just keeps spinning. I can hear the disc slow down and stop and my hard drive light is not blinking at all. I am completely lost. Can anyone help me? It would be hugely appreciated. Thank you. -Stephen

---

### Post by Hedgehog1 on 2011-05-25
There are a number of possible causes.

Can I ask you to do this so we can make you you have open partitions to install Ubuntu?

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

### Post by xx1ndy500xx on 2011-06-28
[CODE]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 14688256 of /dev/sdb for its 
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

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   488,394,751   488,187,904   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         409,640   244,550,271   244,140,632 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda3     244,813,824   488,396,799   243,582,976 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8CB674D8B674C3EC                       ntfs       System Reserved
/dev/sda2        DCF4779DF477789A                       ntfs       
/dev/sdb         0746-DC32                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sdb/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================== sdb: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

=============== sdb: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
[CODE]

Okay sir here are my test results, sorry it took 4 weeks i've been really busy lately :/

---

### Post by oldfred on 2011-06-28
You have a mix of MBR(msdos) and gpt partitions. 

GUID Partition Table detected, but does not seem to be used.

Was this drive part of a MAC? Windows does not work with gpt unless you are using efi to boot like on a MAC or a very new computer.

If you have nothing left the gpt partitions you need to totally houseclean them out so it is pure MBR and then shrink the windows system partition with the windows partition tool. Do not create any new partition just use that to shrink.

Remove old parts of gpt
[http://ubuntuforums.org/showpost.php?p=10022223&postcount=34](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)
Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20

You can also download gdisk and use it:
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by xx1ndy500xx on 2011-06-28
thank you so much fred. i'm going to try the links you hooked me up with. and yes i attempted to install mac on this machine but unfortunately unsuccessful lol thanks again

---

### Post by srs5694 on 2011-06-28
[FixParts](http://www.rodsbooks.com/fixparts/) is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.

Although removing the old GPT data is advisable, such problems don't really match the symptoms you describe; those sound more like you've got a problem with a bad burn of the installation disc. I don't recall offhand if the Ubuntu installer has an option to check its installation disc, but if it does, you could try using that to verify that the disc is OK. If not, you could try using the same computer on which you plan to install to copy the installation disc to a file on your hard disk, just to see if it's readable. If it's not, burn another copy.

---

