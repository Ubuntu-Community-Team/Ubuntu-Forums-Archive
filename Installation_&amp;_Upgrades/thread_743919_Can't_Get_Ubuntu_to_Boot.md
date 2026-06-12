---
title: "Can't Get Ubuntu to Boot"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by erratic on 2008-04-03
Spent the last 2 weeks or so trying to boot Ubuntu off of my 2nd hard drive.  Installation runs fun every time I 've done it regardless of whether I used guided or manual partition to set up the space for Ubuntu.  Originally last week, I first tried using version 7.10 64-bit on the second hard drive and the furthest I ever got in booting was to this error "GRUB Loading stage1.5 Read Error".  I figured this week I would have better luck with using the 8.04 beta 64-bit, but it's the same deal as before minus the reading error.  TO sum it up, it was either that error showing up or it was "Can't find boot device... press f1 to retry press f2 for setup", or something like that every time I tried to boot from the 2nd hd.  I've already gone through several threads and sites that were related to my problem and tried some of the solutions listed in them, but none of them worked.  I've already tried using SGD to boot Ubuntu from there, reinstalling grub in the /boot directory, and installing the 32-bit versions, but no such luck with them.

AS for what I have, here it is:

Dell e510
Motherboard - DM051
80 gb SAMSUNG HD080HJ/P  SATAII HD with WinXP
30 gb WDC WD300BB-00AUA1  IDE HD with Ubuntu

The Bootup sequence in Bios, which has limited options to use, is

1. Floppy
2. Cd-rom
    IDE HD
3. SATA HD
4. USB device

Just so you know, I've already tried installing Ubuntu with the IDE HD part of the bootup sequence, but that did nothing at all as well.  I've also tried installing Ubuntu onto the IDE HD by itself without the SATA HD connected to the motherboard, which I did after removing & plugging back in the motherboard battery and then resetting the bios settings via the jumpers, but that did not work either.  Currently, I'm using WinXP right now while Ubuntu sits unbootable on my 2nd hd.  There's nothing wrong with the 2nd HD since it used to be the main HD for another computer and spent a short time recently as extra storage in my Dell.  Don't want to try upgrading the bios version since I'm out of warranty with Dell and, in case something goes wrong, I want to spend money (I don't have any right now ](*,)  ) on a new motherboard, case, etc instead.  Let's see what else is there?

When I used Gparted or the install program off the live cd of whatever Ubuntu version I used, the drives were listed as SCSI devices under sda (IDE HD) and sdb (SATA HD).  During the 7.10 install, sda was hd(0,0,0) and sdb was hd(0,1,0).  During the 8.04 beta install, sda was hd(0,1,0) and sdb (0,0,0).  Don't know what that's all about.  And finally here's what my menu.lst, device.map, and etc/fstab files say.  Here's hoping a solution can be found since I dig the layout and interface of Ubuntu. Good luck and thx to any who help.  Won't be able to check on or reply to anything you guys post until later tonight due to errands and class.

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
# kopt=root=UUID=264f169c-9e6b-451a-9354-9e8a0ae7c256 ro

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

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=264f169c-9e6b-451a-9354-9e8a0ae7c256 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=264f169c-9e6b-451a-9354-9e8a0ae7c256 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Dell Utility Partition
root		(hd1,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows XP Media Center Edition
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Device.map
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb

etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=264f169c-9e6b-451a-9354-9e8a0ae7c256 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=fb977be7-dc30-47ec-ab5a-b54c42250053 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=07D6-040B  /media/sdb1     vfat    utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=9208069908067D0B /media/sdb2     ntfs    defaults,umask=007,gid=46 0       1
/dev/sdb3       /media/sdb3     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2781027f-746c-495d-bbe2-271e08155a1a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Herman on 2008-04-03
Just try switching the [Hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority")
 in your BIOS and see if it helps.
> There's nothing wrong with the 2nd HD since it used to be the main HD for another computer  Does you PC have 'Cable Select' type IDE cables?
Is your CD/DVD drive daisy-chained on the same IDE cable?
Is your CD/DVD drive jumpered as Master? Or Cable Select?
Is your IDE hard drive jumpered and Master? Or Cable Select?

---

