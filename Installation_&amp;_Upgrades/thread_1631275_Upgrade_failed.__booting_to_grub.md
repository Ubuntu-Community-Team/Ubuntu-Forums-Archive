---
title: "Upgrade failed.  booting to grub"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by DawgMan on 2010-11-26
I did an upgrade from 9.10 to 10.04 via the update manager.

I would not boot after upgrade Error 15: File not found.

I finally got it to boot from an older kernel.

It seemed like something was wrong with the menu.lst (I dual boot w/ XP).  Something about UUID.  According to my previous threads my I was not running grub2.

So I followed this link: 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I did Method 1 and then Method 2.  Now my computer only boots into Grub:

GNU GRUB version 1.98-1ubuntu7

grub>

Do I need to do Method 3?

---

### Post by Rubi1200 on 2010-11-26
Hi,
please boot the computer with the LiveCD and follow the instructions to run the boot info script linked at the bottom of my post.

The results will tell us what is where and make troubleshooting and fixing this a lot easier.

Thanks.

---

### Post by DawgMan on 2010-11-26
RESULTS.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   976,768,064   771,971,445   5 Extended
/dev/sda5         204,796,683   964,847,834   760,051,152  83 Linux
/dev/sda6         964,847,898   976,768,064    11,920,167  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        266C51FD6C51C867                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cd0c7441-38d1-4e1f-a206-b161f7538854   ext3                                     
/dev/sda6        6e553533-d163-46f3-b633-deb66deb8210   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /mnt                     ext3       (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout		5

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
# kopt=root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cd0c7441-38d1-4e1f-a206-b161f7538854

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-25-generic
# root		(hd0,4)
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854	
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet 
# kernel		/boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 ro quiet
splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, memtest86+
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=6e553533-d163-46f3-b633-deb66deb8210 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sda1 /media/Disk2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 362.9GB: boot/grub/core.img
 362.9GB: boot/grub/menu.lst
 362.8GB: boot/grub/stage2
 366.9GB: boot/initrd.img-2.6.28-16-generic
 367.4GB: boot/initrd.img-2.6.31-20-generic
 367.4GB: boot/initrd.img-2.6.32-25-generic
 362.8GB: boot/vmlinuz-2.6.28-16-generic
 374.7GB: boot/vmlinuz-2.6.31-20-generic
 362.9GB: boot/vmlinuz-2.6.32-25-generic
 367.4GB: initrd.img
 362.9GB: vmlinuz

```

---

### Post by Hippytaff on 2010-11-26
Rubi - is the boot flag on the wrong partition? :-)

---

### Post by DawgMan on 2010-11-26
What is rubi?

What partition is it on?

How do  I fix it?

---

### Post by Hippytaff on 2010-11-26
Sorry, I was asking Rubi1200 (the other poster) because I'm not sure if I correctly diagnosed the problem :-)

---

### Post by Rubi1200 on 2010-11-26
> **Hippytaff said:**
> Sorry, I was asking Rubi1200 (the other poster) because I'm not sure if I correctly diagnosed the problem :-)
The boot flag is not the issue here; it is on sda1 where it should be for Windows to function.

The issue here is that there are vestiges of a legacy-GRUB install. Versions later than 9.10 use GRUB2.

@DawgMan:
to correct this problem you need to use the chroot method to purge and reinstall GRUB outlined here:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Obviously, replace the partition number with what is relevant for you; in this case sda5

---

### Post by wilee-nilee on 2010-11-26
> **Rubi1200 said:**
> The boot flag is not the issue here; it is on sda1 where it should be for Windows to function.

The issue here is that there are vestiges of a legacy-GRUB install. Versions later than 9.10 use GRUB2.

@DawgMan:
to correct this problem you need to use the chroot method to purge and reinstall GRUB outlined here:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Obviously, replace the partition number with what is relevant for you; in this case sda5

+1 thats the truth.

---

### Post by DawgMan on 2010-11-26
Purged and Reinstalled Grub 2 from the live CD.

it worked.  Thanks

---

### Post by Hippytaff on 2010-11-26
Cool - I've learned something here too - remember to mark your thread as solved in the thread tools at the top of the page so others can benefit from what you did :-)

---

### Post by Rubi1200 on 2010-11-27
> **DawgMan said:**
> Purged and Reinstalled Grub 2 from the live CD.

it worked.  Thanks
You are more than welcome :)

@Hippytaff:
every day is a learning experience; I am glad you could also benefit from this thread :)

@wilee-nilee: thanks, as ever, for your support :-)

---

