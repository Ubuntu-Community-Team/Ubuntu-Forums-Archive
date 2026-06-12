---
title: "Installation and GRUB"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by bsprowl on 2010-05-29
I know my problem I just don't know how to get control of my computer (Lenovo T61 Laptop) to fix it. 

I removed the 800 MB partition used during the boot process by GRUB 1.5 to list the various options (at least I think that is what this small partition is used for).

If I just turn the system on I get a blank screen - absolutely blank.  If I try to boot from the CD I get a GRUB error 17 no matter what the dike is that I use: Ubuntu ISO, Windows XP install, SUperGRUB, etc.

In any case anything I try to run generates a GRUB 1.5 loading Error 17 which means GRUB cannot find read the partition (but it sees it.)

I've tried UBUNTU 10.04, 8.1, and 9.04, SuperGRUB, UBCB 4.11and GParted 4.3.  They all give me the same error:  "GRUB Loading stage 1.5 GRUB loading. Please wait . . .  Error 17"

I know jut enough Linux to understand my problem but no where near enough to know how to fix it.

(I was very tried when I screwed up and deleted that partition.  I thought I was deleting a partition on a new drive I was setting up to backup everything.  There is nothing of importance on the system as I have complete backups and all of the original software. I would prefer to fix it as it will take several days to rebuild the system and download all of the service packs for XP, Win7, Ubuntu and XANDOS (which were each in their own partition).)

---

### Post by darkod on 2010-05-29
That sounds like you are not actually booting from the cd when trying. Go into BIOS and make sure cd-rom is before hdd.

Then try to boot with the 10.04 cd in live mode, and look around. You can also reinstall grub2 from there if needed.

---

### Post by drs305 on 2010-05-29
If you are getting a Grub error with the LiveCD or other rescue CD you are almost assuredly booting to the hard drive even when you have a CD installed.

During boot, enter your BIOS. This is done by pressing a key, usually one of your function (F1-F12) keys, the ESC or DEL key. The screen may tell you what key to press on the initial screen.

Once in BIOS, go to the boot options and make sure the system is set to first boot to the CD/DVD drive. If it is already set, your CD/DVD drive may be having problems that prevent it from recognizing the inserted disc. If you suspect this and have a commercial disk that you know should boot, try that one just to see if the drive is working.

If you can get to the LiveCD desktop, run this script by meierfra and post the results:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by bsprowl on 2010-05-29
Well duh, of course I needed to fix the boot order. Thanks.

Here are the resuts from running Boot_info-script055.sh:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       118784546 sectors, but according to the info from 
                       fdisk, it has 118797776 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   118,797,839   118,797,777   7 HPFS/NTFS
/dev/sda2         118,784,610   625,136,399   506,351,790   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5         118,784,736   131,090,399    12,305,664  83 Linux
/dev/sda6         131,090,463   179,911,934    48,821,472  83 Linux
/dev/sda7         179,911,998   375,214,139   195,302,142  83 Linux
/dev/sda8         376,852,833   625,137,344   248,284,512   7 HPFS/NTFS

/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda5
the logical partition /dev/sda8 is not contained in the extended partition /dev/sda2

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F858A28558A2426C                       ntfs       Preload                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        32a4d52f-1200-4f43-b4c4-236f24fe452b   ext3                                     
/dev/sda6        2727406d-035b-4db9-8682-2eb17fc96db3   ext3                                     
/dev/sda7        22ce1b28-8b3f-4096-988d-88294002b46c   ext3                                     
/dev/sda8        F2ACB04AACB00ADD                       ntfs       Data-Lenovo                   
/dev/sda: PTTYPE="dos" 
/dev/sdc1        40E9-FEE2                              vfat       Crucial                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/2727406d-035b-4db9-8682-2eb17fc96db3 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/Preload           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/22ce1b28-8b3f-4096-988d-88294002b46c ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda8        /media/Data-Lenovo       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Crucial           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[Boot Loader]
Timeout=5
Default=C:\$WIN_NT$.~BT\BOOTSECT.DAT
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\$WIN_NT$.~BT\BOOTSECT.DAT="Microsoft Windows XP Professional Setup"

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2727406d-035b-4db9-8682-2eb17fc96db3

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		2727406d-035b-4db9-8682-2eb17fc96db3
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		2727406d-035b-4db9-8682-2eb17fc96db3
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2727406d-035b-4db9-8682-2eb17fc96db3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2727406d-035b-4db9-8682-2eb17fc96db3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2727406d-035b-4db9-8682-2eb17fc96db3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2727406d-035b-4db9-8682-2eb17fc96db3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=22ce1b28-8b3f-4096-988d-88294002b46c /home           ext3    relatime        0       2
# /dev/sda9
UUID=32a4d52f-1200-4f43-b4c4-236f24fe452b /tmp            ext3    relatime        0       2
# /dev/sda6
UUID=acdac8aa-36ae-4913-bb49-47a747784d66 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  75.0GB: boot/grub/menu.lst
  75.0GB: boot/grub/stage2
  74.9GB: boot/initrd.img-2.6.27-11-generic
  74.9GB: boot/initrd.img-2.6.27-7-generic
  74.9GB: boot/vmlinuz-2.6.27-11-generic
  74.9GB: boot/vmlinuz-2.6.27-7-generic
  74.9GB: initrd.img
  74.9GB: initrd.img.old
  74.9GB: vmlinuz
  74.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdb" to 4608
ERROR: hpt45x: seeking device "/dev/sdb" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdb" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdb" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdb" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdb" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdb" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdb" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdb" to 137438913024
ERROR: pdc: seeking device "/dev/sdb" to 137438920192
ERROR: pdc: seeking device "/dev/sdb" to 137438927360
ERROR: pdc: seeking device "/dev/sdb" to 137438934528
ERROR: sil: seeking device "/dev/sdb" to 18446744073709551104
ERROR: via: seeking device "/dev/sdb" to 18446744073709551104
ERROR: asr: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdb" to 4608
ERROR: hpt45x: seeking device "/dev/sdb" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdb" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdb" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdb" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdb" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdb" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdb" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdb" to 137438913024
ERROR: pdc: seeking device "/dev/sdb" to 137438920192
ERROR: pdc: seeking device "/dev/sdb" to 137438927360
ERROR: pdc: seeking device "/dev/sdb" to 137438934528
ERROR: sil: seeking device "/dev/sdb" to 18446744073709551104
ERROR: via: seeking device "/dev/sdb" to 18446744073709551104

---

### Post by darkod on 2010-05-30
After deleting one partition grub1 is now looking for its config files at the wrong partition. But that is not a problem, it's easy fix.

This is what is getting me worried:

```
Drive: sda ___________________  __________________________________________________  ___

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 [COLOR=Red]  118,797,839[/COLOR]   118,797,777   7 HPFS/NTFS
/dev/sda2         [COLOR=Red]118,784,610[/COLOR]   [COLOR=Blue]625,136,399[/COLOR]   506,351,790   f W95 Ext d  (LBA)
Extended  partition  linking to another extended partition
/dev/sda5         [COLOR=Red]118,784,736[/COLOR]   131,090,399    12,305,664  83 Linux
/dev/sda6         131,090,463   179,911,934    48,821,472  83 Linux
/dev/sda7         179,911,998   375,214,139   195,302,142  83 Linux
/dev/sda8         376,852,833   [COLOR=Blue]625,137,344[/COLOR]   248,284,512   7 HPFS/NTFS

[COLOR=Red]/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda5
the logical partition /dev/sda8 is not contained in the extended  partition /dev/sda2[/COLOR]
```To resinstall grub1, boot with your 8.10 cd into live mode and in terminal execute:

First you need to open grub prompt with:

sudo grub

Then to reinstall grub on the MBR:

root (hd0,5)
setup (hd0)
quit

Restart and see if that helped. If you get your grub1 boot menu, try whether you can boot all systems you have.

If everything works, don't hurry with repairing the partition table information, but soon you will have to think of a way to repair that mess with the partitions overlapping one another. It's a disaster waiting to happen possibly.

---

### Post by bsprowl on 2010-05-30
Went live with Ubuntu 8.1.
Started grub.  
The first command, root (hd0,5) bought me back to the prompt with no messages so I assume it worked.
setup (hd0) generated the messages:
Quote 
Checking if "/boot/grub/stage1" exists. . . no
Checking if "/grub/stage1" exists. . . no

Error 15: File not found
Unquote

---

### Post by darkod on 2010-05-30
If stage1 is missing I don't know right now. I don't have that much experience with grub1. :)

---

### Post by bsprowl on 2010-05-30
Got it!!!!

Used Find to locate stage1 (found in hd0,6) then root and setup and it boots just fine.

Thanks a bunch.

Bob

---

### Post by darkod on 2010-05-30
> **bsprowl said:**
> Got it!!!!

Used Find to locate stage1 (found in hd0,0) then root and setup and it boots just fine.

Thanks a bunch.

Bob

Sorry, my mistake. I skipped the find step because I thought you don't need it when you know which is your root partition. Obviously I was wrong. As I said, limited knowledge about grub1. :)

Glad you got it sorted.

---

