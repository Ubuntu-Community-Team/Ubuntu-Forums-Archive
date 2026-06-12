---
title: "GRUB refuses to co-exist with my PCI-to-IDE controller."
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by Datalanche on 2006-12-06
Hello, everyone. I've had quite the marathon trying to get this to work. First of all, here's my hard drive setup.

Motherboard IDE controller:
Primary Master: 160gig drive with Windows XP and another ntfs partition
Primary Slave: 250gig with an 25GB ext3 partition I have installed Ubuntu Edgy on, an NTFS partition following that
Secondary Master: DVD+-RW
Secondary Slave: DVD-ROM

I have a Syba Ultra ATA/133 RAID PCI Controller Card - Model #SD-ATA133R, works fine in Linux technically, but anyway, here's what's on it. No RAID used, by the way.
Primary Master: 200 gig NTFS drive
Primary Slave: 160gig ext3 file system with Kubuntu Dapper installed.
Secondary Master: 160 gig NTFS drive
No Secondary Slave

Okay, there's my insane setup. The problem comes in when I try to install Ubuntu, first of all. I would think the two drives on the motherboards controller would be hda and hdb, right? Nope, the controller gets hda through hdd, and those two on the motherboard get hde and hdf. I assume this is the reason for the problem I am having. Whenever I configured my BIOS to boot from SCSI, I could boot Dapper Drake from GRUB, but not Windows. I thought this was because it was booting from that controller, and just saw those drives first. But today, I did some repartitioning so I could install Edgy to a drive on the motherboard's controller and be able to boot Windows and Linux from the grub menu. I decided to install grub to that drive I was installing Edgy on(hde as it appears) since I was weary that it may not work, and just point my BIOS to boot from that one. Well, I did that, and when it was all initially set up, the grub menu popped up, but I couldn't boot EITHER operating system. When I tried to boot them, I got a mix of Error 23 and Error 17's. I didn't think to write it down amidst my frustration. I did some playing around and got Linux to boot by changing the top line of the menu.lst entry for edgy to "root (hd0,0)" which makes even less sense to me.

So yeah, I am confused. There are ways I can work around these issues, but I'd prefer to just use the grub menu as apposed to a bunch of boot discs and all that. Below is the menu.lst I got Edgy to boot off of, but nothing I tried for the XP drive worked, so it is as grub initially set it up. If anyone has a clue, I'd really appreciate it. If you need to know anything else, just let me know. Thanks!

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
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b3eb3d51-8796-47cf-ae58-4a798ec25f3d ro
# kopt_2_6=root=/dev/hdf1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd4,0)

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

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdf1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdf1 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title Ubuntu, kernel 2.6.15-27-k7 (on /dev/hdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-27-k7 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title Ubuntu, kernel 2.6.15-27-k7 (recovery mode) (on /dev/hdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-27-k7 root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.15-27-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title Ubuntu, memtest86+ (on /dev/hdb1)
root (hd1,0)
kernel /boot/memtest86+.bin 
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title Microsoft Windows XP Professional
root (hd3,0)
savedefault
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1
```

---

### Post by violentpuke on 2006-12-07
Syba Ultra ATA/133 RAID PCI Controller Card

Alright i have this same Controller Card with a differnt problem, I am trying to get a raid 1 array to work with ubuntu server, but it can not see the controller and i can not find proper driver support so i can not install to the drives if anyone has any links to a driver that would be great ](*,)

---

