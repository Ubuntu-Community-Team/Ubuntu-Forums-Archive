---
title: "Grub-by Issues - can't find the partition"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by lochok on 2008-07-08
Good Evening,

I've got a PC with two HDs - the 'primary' containing one Windows XP NTFS partition, and the second containing a big NTFS data partition, 2 EXT3 partions (one empty, one with Ubuntu Studio 8.04) and a swap partion.

I'm trying to get it to dual boot between the Ubuntu installation and Windows XP - preferably avoiding modifying the MBR because I had a very nervous evening a couple of weeks ago trying to acomplish the same thing...

I've got Grub hooked into boot.ini - so it can load. However, beyond that has been some issue. Firstly, it couldn't find menu.lst - so I eventually worked out to put it on the EXT3 drive. However, the reigning problem remains that it can't find the EXT3 partition once its open - it is willing to accept (HD1,0) - the big NTFS partition but not (HD1,4), (HD1,5) or (HD1,6) (the partitions various programs say the ext3 one is) and lists Error 5 when I try to root into any of them. Hence, I can't boot into Ubuntu at all, and got a big useless chunk of data on my HD.

Any help would be appreciated.


Lachlan


 The contents of my Menu.lst is displayed below:
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
# kopt=root=UUID=d2a6ef94-bdc6-45ee-9804-302105a197b2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title		Ubuntu 8.04, kernel 2.6.24-16-rt
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=d2a6ef94-bdc6-45ee-9804-302105a197b2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=d2a6ef94-bdc6-45ee-9804-302105a197b2 ro single
initrd		/boot/initrd.img-2.6.24-16-rt

title		Ubuntu 8.04, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by logos34 on 2008-07-08
> **lochok said:**
> 
I've got Grub hooked into boot.ini - so it can load. However, beyond that has been some issue. Firstly, it couldn't find menu.lst - so I eventually worked out to put it on the EXT3 drive. However, the reigning problem remains that it can't find the EXT3 partition once its open - it is willing to accept (HD1,0) - the big NTFS partition but not (HD1,4), (HD1,5) or (HD1,6) (the partitions various programs say the ext3 one is) and lists Error 5 when I try to root into any of them. Hence, I can't boot into Ubuntu at all...

First, please post your 

**sudo fdisk -l**

so we can double check the layout.  But according to menu.lst, windows is the first partition on the first disk (hd0,0)/sda1 and linux the sixth partition on the second disk (hd1,5)/sdb6.

What method did you follow to add ubuntu to boot.ini?

I would suggest installing grub to the MBR of the linux drive and booting from that.  You can chainload windows from there without disturbing the windows bootloader.  Just need to change a couple of things in the XP entry in menu.lst.

---

### Post by lochok on 2008-07-09
> **logos34 said:**
> First, please post your 

**sudo fdisk -l**

so we can double check the layout.  But according to menu.lst, windows is the first partition on the first disk (hd0,0)/sda1 and linux the sixth partition on the second disk (hd1,5)/sdb6.

What method did you follow to add ubuntu to boot.ini?

I would suggest installing grub to the MBR of the linux drive and booting from that.  You can chainload windows from there without disturbing the windows bootloader.  Just need to change a couple of things in the XP entry in menu.lst.

I ran that command, as well as Geometry in Grub in linux, and Grub while booting. Grub in Linux = Fdisk, but was different to the one when boot loading! Various partitioning programs are giving me errors and so forth - the HD has bigger issues methinx. But it's odd, because Windows and the Ubuntu Live CD can read them fine...

I've for now reformatted the drives and am going to try for a wubi installation...

Thanks for your help


Lochok

---

### Post by logos34 on 2008-07-09
ok, whatever

---

