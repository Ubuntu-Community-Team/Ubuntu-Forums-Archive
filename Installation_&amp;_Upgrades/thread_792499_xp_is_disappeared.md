---
title: "xp is disappeared"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by mithritades on 2008-05-13
i was running a dual boot and when i switched back over to windows xp,it's been erased or something. Do i have to re-install xp an will it interfere with the ubuntu installation?

---

### Post by iaculallad on 2008-05-13
Open your GRUB file and post what it says:

sudo gedit /boot/grub/menu.lst

---

### Post by mithritades on 2008-05-13
then?...thats all i have to do?

---

### Post by iaculallad on 2008-05-13
Just post your GRUB content of your /boot/grub/menu.lst so we could take a look if errors could be found there. That's the first place to start with errors like that.

---

### Post by zvacet on 2008-05-13
```
sudo fdisk -l
```

Post it here.You probably just need to add win partition to the grub.Nothing to be worried about.

---

### Post by mithritades on 2008-05-13
owner@ubuntu:~$ sudo fdisk -l
[sudo] password for owner:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcda57b2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS
owner@ubuntu:~$ 

thats from:sudo fdisk -l

---

### Post by mithritades on 2008-05-13
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'boot'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

## should update-grub add boot to the default options
## can be true or false
# boot=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.22-14-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.22-14-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot

---

### Post by mithritades on 2008-05-14
if i re-install my windows XP from the disc will it interfere with my ubuntu partion when i reboot?

---

### Post by logos34 on 2008-05-14
xp is still there, because you're running ubuntu on Wubi INSIDE windows partition. As far as fixing it so you can boot back into xp goes, i'm not sure...

---

### Post by sunstriker on 2008-05-14
The windows bootloader should show you the options windows xp and ubuntu. Anyway your windows can't be gone. Since you're using wubi, ubuntu resides into windows. Maybe your windows bootloader has some faulty errors, like not showing you the menu. Try pressing F8 when you boot..

---

### Post by mithritades on 2008-05-14
i tried everything in the F8 menu and it still comes up a blue screen with no desktop icons,only thing on my desktop that's left is the recycle bin...

---

