---
title: "[SOLVED] Hang on loading Kernel"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by drlock on 2007-10-09
I am having a bear of a time installing installing Ubuntu on a brand new Dell OptiPlex 320.  The LiveCD (7.04) booted and installed just fine.  I can reboot and load Grub just fine, but as soon as a choose Ubuntu I get just a blinking cursor. (Booting Win XP works fine)

I tried going to the Grub command line and entering the command manually.  As soon as I enter:
```
kernel /boot/vmlinuz... root=/dev/sda1
```
and hit enter it just hangs. (I use tab complete so I know it can read the HD and that the vmlinuz file is correct.)

I have seen a good deal of discussion on some problems that sound similar:
[http://ubuntuforums.org/showthread.php?t=216039](http://ubuntuforums.org/showthread.php?t=216039)
[http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115)
and have tried all the suggestions I could find:
[LIST]
[*] I tried the Alt. CD with the same result
[*] The install already used UUID.  I double checked it, but that did not help.
[*] I tried adding the following options to the kernel command: ide=nodma acpi=off irqpoll linux no-hlt
[*] I do not have any IDE drives, just one SATA HD and one SATA CD/DVD RW
[*] My BIOS does not seem to have an option to disable legacy USB.
[/LIST]
None of those seemed to help.

I am all out of ideas, but am hoping someone can give me some help.

I will try and post some system and debug information in a couple minutes.

Thanks

---

### Post by drlock on 2007-10-09
Okay here is my debugging information ...

Output from: sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5569    44732961    7  HPFS/NTFS
/dev/sda2            5570        9549    31969350   83  Linux
/dev/sda3            9550        9726     1421752+   5  Extended
/dev/sda5            9550        9726     1421721   82  Linux swap / Solaris


Output of: sudo /sbin/dumpe2fs /dev/sda2 | grep UUID
dumpe2fs 1.40-WIP (14-Nov-2006)
Filesystem UUID:          b66aeedc-9bd7-418f-8523-607f849028ae

Contents of my /boot/grub/menu.lst:
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
# kopt=root=UUID=b66aeedc-9bd7-418f-8523-607f849028ae ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b66aeedc-9bd7-418f-8523-607f849028ae ro quiet irqpoll splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b66aeedc-9bd7-418f-8523-607f849028ae ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
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


Thanks for your help

---

### Post by drlock on 2007-10-12
For those who find this thread in the future, it turns out my problem was that I was trying to install on a Dell Optiplex 320.  Grub does not work properly on this machine.  You need to install lilo or grub2, see this post for instructions: [http://ubuntuforums.org/showthread.php?t=409345&page=2](http://ubuntuforums.org/showthread.php?t=409345&page=2)

---

