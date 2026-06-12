---
title: "Slow boot after upgrade to 10.04"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by wmwong on 2010-11-11
Hi,

10.04 boasts a very quick boot time, but after upgrading, I've been having a much slower boot than in 9.10. It hangs at the screen when it says

Boot from (hd1, 0) ext3
Starting up...

It stays at this screen for a good 15 seconds before showing me the login screen. I've attached the results from a boot info script.

Any ideas would be greatly appreciated.

Thanks,
Wesley

---

### Post by wilee-nilee on 2010-11-11
For all to see. And can you give a little more actual time from power on to your at the login or desktop. since you have a dual boot you have a auto 10 sec wait alone at grub. Also you have grub-legacy and ext3 partitions. To be honest I would back it up and do a fresh install it will run much better (probably). Upgrades are convenient but there have been changes you don't have=grub2 and ext type, and just upgrading if you don't clean up the debris can slow down the setup.
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   612,992,204   612,992,142  83 Linux
/dev/sdb2         612,992,205   625,137,344    12,145,140   5 Extended
/dev/sdb5         612,992,268   625,137,344    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DEE03B87E03B6545                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        63ecedb2-5534-4f3f-8c18-d98d7001b9df   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0155bd16-6de6-410c-b18b-bd13aa071e34   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=63ecedb2-5534-4f3f-8c18-d98d7001b9df

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-16-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.27-14-generic
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.27-14-generic (recovery mode)
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		63ecedb2-5534-4f3f-8c18-d98d7001b9df
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


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=63ecedb2-5534-4f3f-8c18-d98d7001b9df /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=0155bd16-6de6-410c-b18b-bd13aa071e34 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   6.4GB: boot/grub/menu.lst
   6.4GB: boot/grub/stage2
   7.7GB: boot/initrd.img-2.6.27-14-generic
   6.7GB: boot/initrd.img-2.6.28-16-generic
   8.5GB: boot/initrd.img-2.6.31-21-generic
   8.5GB: boot/initrd.img-2.6.32-21-generic
   6.5GB: boot/initrd.img-2.6.32-22-generic
   6.5GB: boot/initrd.img-2.6.32-23-generic
   7.4GB: boot/initrd.img-2.6.32-24-generic
  48.7GB: boot/vmlinuz-2.6.27-14-generic
  76.2GB: boot/vmlinuz-2.6.28-16-generic
   6.7GB: boot/vmlinuz-2.6.31-21-generic
   6.9GB: boot/vmlinuz-2.6.32-21-generic
   6.6GB: boot/vmlinuz-2.6.32-22-generic
   6.4GB: boot/vmlinuz-2.6.32-23-generic
   7.4GB: boot/vmlinuz-2.6.32-24-generic
   7.4GB: initrd.img
   6.5GB: initrd.img.old
   7.4GB: vmlinuz
   6.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by wmwong on 2010-11-11
Thanks for the reply wilee-nilee. I think I've been upgrading since 8.04 without a fresh install since. I do have a 10 second wait at the grub screen, but the 15 second wait I was referring to was at the 'Starting up...' screen. It doesn't include the rest of the startup process.

Hopefully, there is a way to fix this without the fresh install. Unfortunately, at the time I installed, I didn't put my home directory in it's own partition. A fresh install for me would be a last resort.

---

### Post by wilee-nilee on 2010-11-11
> **wmwong said:**
> Thanks for the reply wilee-nilee. I think I've been upgrading since 8.04 without a fresh install since. I do have a 10 second wait at the grub screen, but the 15 second wait I was referring to was at the 'Starting up...' screen. It doesn't include the rest of the startup process.

Hopefully, there is a way to fix this without the fresh install. Unfortunately, at the time I installed, I didn't put my home directory in it's own partition. A fresh install for me would be a last resort.

Do yourself a favor get a external HD and image the whole thing, and back up what you need at some point. I realize that is easy for me to say, but if your computer HD went bad and was not recoverable, how would you feel about that.

My wait is at least 15 seconds from hitting the OS in Maverick and W7, I wonder if this isn't more of a it's supposed to be faster but it's not are you really sure, and really this amount of time seems trivial, I would be more worried about getting that thing backed up no matter what.

---

### Post by wmwong on 2010-11-13
You're right about backing up. I know I should, but it's always one of those things you procrastinate until it's too late.

As for thinking the startup is slow rather than it is slow, I'm pretty sure it is slow. This doesn't take into account the fact that after I type my password into the login, it takes me 20 seconds before I can even start Chrome because my panels don't show up (that's another problem to solve...). I use 10.04 at work as well and it boots up lightning fast.

I guess it looks like the only way is to do a fresh install. Time to suck it up and buckle down.

Thanks for the help wilee-nilee.

---

