---
title: "switched to 32 bit, 64 bit kernel still loads"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2007-01-21
I got sick of Kubuntu 64 bit and decided to switch to a 32 bit installation.
So I backed up everything I could and installed a new system on / from a 32-bit CD. Everything went OK until I booted up and the mouse wouldn't work. I went to install some nvidia drivers and got the message that the (32-bit) drivers didn't match my (64-bit) architecture. Sure enough, **uname -a** tells me I'm still using a 64-bit kernel.

Now when installing I simply told the installer to use / as the installation point and must have forgotten to give any information about which kernel to use/install or where to boot from. I have a boot partition on /boot which, when I look at it, has not been updated in the last month. So I assume the installer either didn't install any kernel or put it somewhere else.

What's my best option at this stage? How can I replace the kernel in /boot with a 32-bit one?

For info, here's my fstab file from before the 32-bit installation
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=23cd75dd-8522-4cc8-8026-43d34facd54f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=38771644-df5d-4863-95ef-4abcf0a9c696 /boot           ext3    defaults        0       2
# /dev/sda4
UUID=6aca9cac-5354-4183-bf88-68e9e62bed9a /home           ext3    defaults        0       2
# /dev/hda6
UUID=f3466d96-c519-11d7-9a37-a027fa319c88 /media/oldhome  ext3    defaults        0       2
# /dev/hda7
UUID=bb8c5418-a024-4cc0-a287-4b1b083042af /media/videos ext3    defaults        0       2
# /dev/hdb1
/dev/hdb1   /media/supersize   ext3   defaults   0   2
# /dev/sda5
UUID=7db0edf9-d00d-4b15-a5c3-c738a9091488 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

I overwrote the automatically created /etc/fstab file with this, perhaps unwisely.

The menu.lst file in /boot/grub looks like this:

```

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
color cyan/blue white/blue

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
# kopt=root=UUID=23cd75dd-8522-4cc8-8026-43d34facd54f ro
# kopt_2_6=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, kernel 2.6.12-10-386 (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda7 ro single 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, kernel 2.6.12-9-386 (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda7 ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Ubuntu, memtest86+ (on /dev/hda7)
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

