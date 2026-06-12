---
title: "Intalled Fiesty on 2 Volumes - How to Get Volume Back"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by pushin50 on 2008-01-22
Total Newb!

In XP, hadthree partitions, one for Dell, one for XP and one for Freespire. Made two new partitions - thought that was required to give ubuntu a boot and a swap partition. Eventually blew away XP but I don't care. Love ubuntu!

Apparently ubuntu partial disk installation also wiped out my original GRUB file by installing into Freespire partition. Had GRUB from Freespire originally. Ubuntu installation overwrote my original GRUB so I hung at GRUB error 17.

Attempted ubuntu installation allowing it to grab full disk had a fatal error.  So, re-installed ubuntu, this time allowing it to use part of disk. Now ubuntu works great but . . .

if I go to Places\Computer, I have a File System Volume but, also, a "13.6 GB Volume". That volume has a duplicate 7.04 file system in it. GRUB's menu.lst file appears to be identical in both places and, I think, is telling me that I have duplicate installations.

SCSI HD is 30GB. I'd like to rationalize my system to get rid of the duplication and unify the volumes into a single volume usable by most recently installed ubuntu File System.

Concern is that if I use gparted to delete the partition with the prior ubuntu 7.04, I might delete the GRUB file that the boot is looking for. How can I avoid that?

Here's the GRUB file:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=001b5bf7-2460-4e74-9029-ddb1045f3c6b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=001b5bf7-2460-4e74-9029-ddb1045f3c6b ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=001b5bf7-2460-4e74-9029-ddb1045f3c6b ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=001b5bf7-2460-4e74-9029-ddb1045f3c6b ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=001b5bf7-2460-4e74-9029-ddb1045f3c6b ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.04 (7.04) (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sda1
initrd /boot/initrd.img-2.6.20-15-generic
savedefault
boot


I also loaded KDiskFree. It shows, aside from removable media:

/dev/sda3, type=?, size=12.GB, mount pt=/
UUID= 001b5bf7 . . ., type=ext3, size=N/A, mount pt=/, Free=0
lrm, type=?, size=188.2MB, mount pt=/lib/module, Free=155.2
udev, type=?, size=188.2MB, mount pt=/dev, Free=188.1
varlock, type=?, size=188.2MB, mount pt=/var/lock, Free=188.2
varrun, type=?, size=188.2MB, mount pt=/var/run, Free=188.1

Any help for me out there? Thank you so much.

Chris

---

### Post by Partyboi2 on 2008-01-22
You could delete the partition you are wanting to then reinstall grub if you need to via the[ live cd ]("http://ubuntuforums.org/showthread.php?t=224351")
or try [super grub]("http://supergrub.forjamari.linex.org/")

---

### Post by pushin50 on 2008-01-23
Thanks partyboi2. Wish I'd known about supergrub sooner. would have saved myself a lot of grief . . . but then, I wouldn't have learned so much either.

---

### Post by pushin50 on 2008-01-29
partyboi2,

Over the weekend dowload supergrub and gnome partition editor live CDs. Partition editor worked great - resized the partition with 7.04 file system, killed a redundant ubuntu swap partition left from the prior installation. Now left with one file system partition and a swap - nice and clean and works great. Did not need to use supergrub but it's nice to have the CD on hand.

Upgraded to gutsy and that worked as well.

In short, I'm off and rocking. Thank you so much.

---

### Post by Partyboi2 on 2008-01-29
glad you are up and running. :)

---

