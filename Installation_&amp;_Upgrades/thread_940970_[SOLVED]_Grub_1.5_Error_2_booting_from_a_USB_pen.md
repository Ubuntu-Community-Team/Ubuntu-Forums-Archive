---
title: "[SOLVED] Grub 1.5 Error 2 booting from a USB pen"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by dirty_ol_rza on 2008-10-07
I've installed Hardy onto a 8gig USB pen but when trying to boot from it I get a an error 2 at stage 1.5





sudo fdisk -lu

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders, total 231496650 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       191928555   192426569      249007+  82  Linux swap / Solaris
/dev/sda2       192426570   231496649    19535040   83  Linux
/dev/sda3   *          63   191928554    95964246    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 8254 MB, 8254390272 bytes
255 heads, 63 sectors/track, 1003 cylinders, total 16121856 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9455a115

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15326009     7662973+  83  Linux
/dev/sdb2        15326010    16113194      393592+   5  Extended
/dev/sdb5        15326073    16113194      393561   82  Linux swap / Solaris





/media/disk/boot/grub


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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=e69b5f83-8332-4a6e-9572-74efe2369a8b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e69b5f83-8332-4a6e-9572-74efe2369a8b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e69b5f83-8332-4a6e-9572-74efe2369a8b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




Any ideas or thoughts would be appreciated.

---

### Post by Pumalite on 2008-10-07
Check:
[http://users.bigpond.net.au/hermanzone/p15.htm#2_](http://users.bigpond.net.au/hermanzone/p15.htm#2_)
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by caljohnsmith on 2008-10-07
Have you been able to boot from a USB drive before on your computer, or is this your first try? Have you confirmed in your BIOS that you are booting the USB drive before your sda drive? Also, try the following to reinstall Grub to your flash drive's MBR (Master Boot Record):
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Post the output of all the above commands, reboot, and let us know what happens.

---

### Post by dirty_ol_rza on 2008-10-07
Thanks a lot, that's fixed it

---

