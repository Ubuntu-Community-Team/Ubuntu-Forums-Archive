---
title: "[SOLVED] cannot boot windows after kernel upgrade"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by klemencic on 2007-12-30
I have a new install of Ubuntu and last night I left the machine running to download and install 174 updates
When I tried to reboot, there were new entries in the Grub menu for kernel 2.6.20.16 but when I tried to boot these or kernel 2.6.20.15 I received a unable to mount error
I fixed this by changing menu.lst to read root (2,0) instead of root (0,0) but when I try to boot the windows partition i receive the error ' invalid or unsupported executable format'

Below is output of fdisk -l and menu.lst

/dev/hdb is the Utumbu system i am using
/dev/hdc contains the windows partition i wish to boot
/dev/hdd is a Utumbu system I was using before I decided I was going to stick with Linux.  This is now going to be a spare data drive

In menu.lst, the 4 lines I marked *** were not in my previous menu.lst, they were added with the new kernel

Also is there any way I can stop grub from changing the configuration when it does a kernel upgrade


Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4689    37664361   83  Linux
/dev/hdb2            4690        4865     1413720    5  Extended
/dev/hdb5            4690        4865     1413688+  82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
81 heads, 63 sectors/track, 30629 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          42       14890    37887192    7  HPFS/NTFS
/dev/hdc2           14891       14930      102060   83  Linux
/dev/hdc3              14          41       71410+  16  Hidden FAT16
/dev/hdc4           14931       30629    40055998+   f  W95 Ext'd (LBA)
/dev/hdc5           14931       30629    40055967   8e  Linux LVM

Partition table entries are not in disk order

Disk /dev/hdd: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         494     3968023+  83  Linux
/dev/hdd2             495         524      240975    5  Extended
/dev/hdd5             495         524      240943+  82  Linux swap / Solaris
klem@Homer:~$ 



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
default		4

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
# kopt=root=UUID=044d17d1-198c-4019-85bb-0f771d914888 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=044d17d1-198c-4019-85bb-0f771d914888 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=044d17d1-198c-4019-85bb-0f771d914888 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=044d17d1-198c-4019-85bb-0f771d914888 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=044d17d1-198c-4019-85bb-0f771d914888 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows 2000 Professional
root		(hd1,0)
***savedefault
***makeactive
***map		(hd0) (hd1)
***map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd1.
title		Ubuntu 7.10 (7.10) (on /dev/hdd1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hdd1 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot

---

### Post by klemencic on 2007-12-30
sorry this is fixed there were new posts in one of my previous threads which solved the problem

---

