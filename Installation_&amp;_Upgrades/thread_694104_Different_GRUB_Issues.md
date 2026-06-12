---
title: "Different GRUB Issues"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by Kubotaz4 on 2008-02-11
This post is goign to be long, so bare with me

I have 2 Hd's

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       19012   152657662+   7  HPFS/NTFS
/dev/sda3           19013       19452     3534300   db  CP/M / CTOS / ...

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38536   309540388+  83  Linux
/dev/sdb2           38537       38913     3028252+   5  Extended
/dev/sdb5           38537       38913     3028221   82  Linux swap / Solaris


The HD that came with the computer has XP.  I bought a new Hd and installed Ububntu 6.06 LTS.  Both OS's work fine and can boot to whichever, but I dl'ed 7.10 and wanted to put it on the HD with XP, but when I changed boot sequence to read off CD-ROM, I got the Error 25 message, tried a few more times, then got the Error 17 message.  I have read that the GRUB might be located on the wrong HD?  The goal is to get 7.10 on the 160 gig HD and eventually merge both HD's to one OS.  Thanks!


other information that might help..

jay@jay-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu, kernel 2.6.15-51-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-51-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-51-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-51-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-51-386 root=/dev/sdb1 ro single
initrd          /boot/initrd.img-2.6.15-51-386
boot

title           Ubuntu, kernel 2.6.15-29-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-29-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/sdb1 ro single
initrd          /boot/initrd.img-2.6.15-29-386
boot

title           Ubuntu, kernel 2.6.15-28-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sdb1 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

jay@jay-desktop:~$

---

