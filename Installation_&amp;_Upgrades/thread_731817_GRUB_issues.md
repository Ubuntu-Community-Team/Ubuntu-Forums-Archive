---
title: "GRUB issues"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by BlackLight94 on 2008-03-22
So first off, let me say that I just switched to Ubuntu since i got a new modem that was supported. I am running 7.10 and here is my problem:

I had windows installed when I installed Ubuntu and it was fine. Then after I got all of the drivers that I needed for Ubuntu from my windows installation. After I got the drivers up and running, I decided to make a full switch to Ubuntu, but now when GRUB loads, it still displays the Windows XP installation a a choice to boot from. Any suggestions?

---

### Post by banewman on 2008-03-22
Did you remove the windows partition?

---

### Post by tad1073 on 2008-03-22
You need to sudo into /boot /grub/menu.lst and remove the entry. But be carefull as you could realy mess things up.

---

### Post by Terminating.proprietary on 2008-03-22
I am a complete newb to Linux, but perhaps there is a Linux equivalent to fixmbr in Windows?

---

### Post by Pumalite on 2008-03-22
Backup your file first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
gksudo gedit /boot/grub/menu.lst
Edit your menu.lst:
Comment out (put a # in front of the Windows entry)
Save, exit, reboot.

---

### Post by BlackLight94 on 2008-03-22
Okay so right now my menu.lst file is:

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
# kopt=root=UUID=eadbcad6-8d80-412f-93a7-b398ba8d847f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=eadbcad6-8d80-412f-93a7-b398ba8d847f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=eadbcad6-8d80-412f-93a7-b398ba8d847f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

so I would change it to........


and BTW thanks A LOT I didn't expect to get so many replies so fast

---

### Post by BlackLight94 on 2008-03-22
All the cool faces in the above post are supposed to be and eight between parenthesis

---

### Post by Pumalite on 2008-03-22
To this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title Microsoft Windows XP Home Edition
#root (hd0,0)
#savedefault
#makeactive
#chainloader +1

---

### Post by Kiri on 2008-03-22
Put comment hashes #
In front of the lines in the last part:

> title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1


EDIT: Do what pumalite said :)

---

### Post by BlackLight94 on 2008-03-22
Thanks, I'm rebooting now

---

