---
title: "Booting Linspire"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by compugen on 2006-09-04
I am having trouble booting the LINSPIRE from my pc.
I am having following::

/boot of 1GiB as hda1
/ for Ubuntu of 5GiB as hda2
/swap of 1Gig at teh drive's end
/ for Linspire as HDA6

I installed linspire first after partitioning and then UBUNTU. Now ubuntu shows linspire in its GRUB menu but it doesnt boot it up. Also, in FSTAB entry for HDA5 -- the root of the LINSPIRE, is mounted as /media/hda5.

Any help is really appreciated.

---

### Post by john_spiral on 2006-09-04
run a **sudo fdisk -l** on the machine and post results.

also post contents of grub **menu.lst** file, there might be more than one one the machine figure out which one is active. 

john

---

### Post by compugen on 2006-09-05
Thanks for the reply. Here are the details:

[U]sudo fdisk -l
[/U]
```
[COLOR="Blue"]Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         127     1020096   83  Linux
/dev/hda2             128         781     5253255   83  Linux
/dev/hda3             782        4742    31816732+   5  Extended
/dev/hda4            4743        4870     1028160   82  Linux swap / Solaris
/dev/hda5             782        1546     6144831   83  Linux
/dev/hda6            2852        4742    15189426    b  W95 FAT32
[/COLOR]
```

_Menu.lst on /dev/hda1 (boot partition)_
```

[COLOR="Blue"]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Debian GNU/Linux (3.1) (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.14 root=/dev/hda5 
savedefault
boot

[/COLOR]
```

Here is the entry that is there in the linspire partition (/dev/hda5)

Menu.lst
```
[COLOR="Blue"]# Generated by jiffyboot version 8.172. If this file is edited, the
# system will stop modifying it.  To allow the system to resume
# management of this file, remove it and run /sbin/jiffyboot

default=0
timeout=0
fallback 

title hidden
configfile (hd0,4)/boot/grub/menu-normal.lst
[/COLOR]

menu-normal.lst

# Generated by jiffyboot version 8.172. If this file is edited, the
# system will stop modifying it.  To allow the system to resume
# management of this file, remove it and run /sbin/jiffyboot

default=0
timeout=10
color cyan/green magenta/green
splashimage=/boot/grub/bootsplash.xpm.gz

instructions Use the %c and %c keys to select which entry is highlighted.
timeout_message Entry %d will be booted automatically in %d seconds.

# hda5, boot entry
title Linspire 5.1.427
root (hd0,4)
kernel /boot/vmlinuz-2.6.14  root=/dev/ide/host0/bus0/target0/lun0/part5 rootdev=0x0305 ramdisk=33792 video=vesafb:nomtrr jiffymount=noatime resume2=swap:/dev/hda5:0x44000 vga=0x311 splash=silent
initrd /boot/initrd-2.6.14.gz

# hda5, diagnostic boot entry of /dev/ide/host0/bus0/target0/lun0/part5
title Diagnostics
root (hd0,4)
kernel /boot/vmlinuz-2.6.14 noresume2 single Diagnostics splash=0  root=/dev/ide/host0/bus0/target0/lun0/part5 rootdev=0x0305 ramdisk=33792 video=vesafb:nomtrr jiffymount=noatime resume2=swap:/dev/hda5:0x44000
initrd /boot/initrd-2.6.14.gz

# hda5, redetect boot entry of /dev/ide/host0/bus0/target0/lun0/part5
title Redetect
root (hd0,4)
kernel /boot/vmlinuz-2.6.14 noresume2 redetect splash=0  root=/dev/ide/host0/bus0/target0/lun0/part5 rootdev=0x0305 ramdisk=33792 video=vesafb:nomtrr jiffymount=noatime resume2=swap:/dev/hda5:0x44000
initrd /boot/initrd-2.6.14.gz

title Advanced Menu
configfile (hd0,4)/boot/grub/advanced-normal.lst

```

This is the fstab file in the ubuntu partition.
[COLOR="Blue"]```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda5       /media/hda5     reiserfs defaults        0       2
/dev/hda6       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```[/COLOR]

[COLOR="Black"]The basic structure that I had in my mind was to enable UBUNTU as the primary OS for me and Linspire for my sis as she is beginner and had been using windows ever since. For fat32 partition, the idea was to share the data between the two OS and windows, since both of them will be reading the data from FAT32 partition; provided it is upto 32Gb.[/COLOR]

Thanks again for the help. Let me know if i should forward anything else.

---

### Post by john_spiral on 2006-09-07
did you get up and running?

Try plonkking:

# hda5, boot entry
title Linspire 5.1.427
root (hd0,4)
kernel /boot/vmlinuz-2.6.14  root=/dev/ide/host0/bus0/target0/lun0/part5 rootdev=0x0305 ramdisk=33792 video=vesafb:nomtrr jiffymount=noatime resume2=swap:/dev/hda5:0x44000 vga=0x311 splash=silent
initrd /boot/initrd-2.6.14.gz

in the menu.lst on /dev/hda1, should boot.

Johne

---

### Post by compugen on 2006-09-07
Alrite.. booted it. But I did something else. I placed the link to the menu.lst of the hda5 in the boot menu. Now first it gets me to grub and then to the Linspire Menu (LiLo). You think this is some kinda harm or something?

Also, if it can be a possibility to boot it from my usb since I am having around 5 USB externals and if I can get linux running on them, to be able to boot from USB.. it would be great. 

Thanks Johne.. I tried your option the moment I saw it and it worked. Now which version should i keep -- my stupid trick or your thought version? Any trade offs between the two?

---

### Post by john_spiral on 2006-09-12
boot loaders like LILO and GRUB don't take up any memory once their job is done, so it doesn't really matter what method you use.

can you explain in more detail what method you devised, it's always good to learn something new.
 

try [http://www.simonf.com/usb/](http://www.simonf.com/usb/) for more info on booting linux on a usb drive, happy reading!

---

### Post by compugen on 2006-09-13
This is what I did.

Situation:
Booting Linspire from a UBUNTU, GRUB based menu.

Requisite:
Ubuntu, Linspire installed.

Procedure:
Installed UBUNTU. Did partitioning through UBUNTU installation process. Installed linspire with the expert options; under expert unchecked WRITE MBR which did not mess UBUNTUs mbr.
Now I had two OS in seperate partitions with their own inits and vm kernels installed onto their partitions.

Solution for linspire booting:
In ubuntu grub file i mentioned one link to the menu.lst of the Linspire on linspire partition.


If my new grub menu file is required I'll update is as well. Let me know if it is required.

---

