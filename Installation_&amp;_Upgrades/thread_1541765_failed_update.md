---
title: "failed update"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by scotch_neat on 2010-07-29
I am running dual boot Win XP / Ubuntu. I tried to update to 10 using the updater, but it exited before the end and now I cannot get a desktop. Windows still boots fine. I know NOTHING about programming (grub??). All the threads I've seen are all Greek to me. I can't even tell you what the problem is. Is there any possibility that I could copy/paste the folders from the live CD File System to my drive? 

Please help.
Thanks
Stephen

---

### Post by scotch_neat on 2010-07-31
> **scotch_neat said:**
> I am running dual boot Win XP / Ubuntu. I tried to update to 10 using the updater, but it exited before the end and now I cannot get a desktop. Windows still boots fine. I know NOTHING about programming (grub??). All the threads I've seen are all Greek to me. I can't even tell you what the problem is. Is there any possibility that I could copy/paste the folders from the live CD File System to my drive? 

Please help.
Thanks
Stephen

Okay, I've gotten no replies so far, so how about a different question?

If my update from 8 to 10 failed, can I still run an update from Live CD without losing my files? Or do I have to back up all files and do a full install?

Please, someone help me, I have no programming experience and do not want to lose my files.

Thanks very much.
Stephen

---

### Post by scotch_neat on 2010-08-01
All right. I have run Boot Info Script. Here are the results.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    50,058,539    50,058,477   7 HPFS/NTFS
/dev/sda2          50,058,540   151,862,444   101,803,905  83 Linux
/dev/sda3         151,862,445   156,296,384     4,433,940   5 Extended
/dev/sda5         151,862,508   156,296,384     4,433,877  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8013 MB, 8013217792 bytes
5 heads, 32 sectors/track, 97817 cylinders, total 15650816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,064    15,650,815    15,642,752   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        300047D50047A0A8                       ntfs                                     
/dev/sda2        e40ecfb8-9715-42ba-bc01-f2346ed90d21   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9801b4b6-5550-44f7-bd2c-51cd2041d1b7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        75B2-ED0A                              vfat       MINI                          
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/300047D50047A0A8  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/e40ecfb8-9715-42ba-bc01-f2346ed90d21 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/MINI              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=e40ecfb8-9715-42ba-bc01-f2346ed90d21 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=e40ecfb8-9715-42ba-bc01-f2346ed90d21 ro quiet splash
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=e40ecfb8-9715-42ba-bc01-f2346ed90d21 ro single

title		Ubuntu 10.04 LTS, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e40ecfb8-9715-42ba-bc01-f2346ed90d21 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e40ecfb8-9715-42ba-bc01-f2346ed90d21 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 10.04 LTS, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e40ecfb8-9715-42ba-bc01-f2346ed90d21 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e40ecfb8-9715-42ba-bc01-f2346ed90d21 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 10.04 LTS, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

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


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=e40ecfb8-9715-42ba-bc01-f2346ed90d21 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=9801b4b6-5550-44f7-bd2c-51cd2041d1b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sda2: Location of files loaded by Grub: ===================


  28.4GB: boot/grub/menu.lst
  28.3GB: boot/grub/stage2
  28.3GB: boot/initrd.img-2.6.22-14-generic
  28.3GB: boot/initrd.img-2.6.22-14-generic.bak
  28.4GB: boot/initrd.img-2.6.24-16-generic
  28.3GB: boot/initrd.img-2.6.24-16-generic.bak
  28.3GB: boot/vmlinuz-2.6.22-14-generic
  28.4GB: boot/vmlinuz-2.6.24-16-generic
  28.3GB: boot/vmlinuz-2.6.32-21-generic
  28.4GB: initrd.img
  28.3GB: initrd.img.old
  28.4GB: vmlinuz
  28.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
__________________________________________________________

Currently running Ubuntu 10 off LIVE CD.

I see that in partition 2 where Ubuntu is, there is no boot loader.

Can anyone tell me how to fix this? 

I cannot seem to access some folders to back them up so I am concerned about having to do a full install. I can see them with sudo but don't know how to change the permissions/ownership to move/copy them. If I could do that then I can back them up and do the full install.

Thanks very much.
Stephen

---

### Post by scotch_neat on 2010-08-01
> **scotch_neat said:**
> Okay, I've gotten no replies so far, so how about a different question?

If my update from 8 to 10 failed, can I still run an update from Live CD without losing my files? Or do I have to back up all files and do a full install?

Please, someone help me, I have no programming experience and do not want to lose my files.

Thanks very much.
Stephen

Another question: if I run Update Manager and install the updates, will that fix my system?

---

