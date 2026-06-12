---
title: "FYI: NVidia Graphic Cards Problem/Solution"
date: 2005-02-21
forum: Installation &amp; Upgrades
---

### Post by Tyche on 2005-02-21
PROBLEM:  Unreadable text in secondary installation - unable to finish the Ubuntu installation.

I have had difficulty installing Ubuntu (Warty).  The problem was that, when the installation re-booted to finish the installation, I was unable to read the text.

MACHINE:
Pentium PIII/750 MgHertz
500 Mg RAM
Tyan S1850 Trinity MotherBoard
SamSung SyncMaster 712N Flat Panel Monitor
**_NVidia GForce4 MX420 Video Board_**

This last is important.  Recently, various distributions of Linux have had trouble installing when an NVidia board was present.

SOLUTION:
I used the Ubuntu LiveCD to see what that grub menu.lst and the menu.lst in my installation each read.  One significant difference is that the LiveCD included an options file.  More significantly, the LiveCD included driver and resolution setups in the menu.lst for various graphics boards **_INCLUDING NVIDIA._**.  By using the "generic" NVidia driver (nv) and a screen resolution of 1024x768, I was finally able to complete the installation

SUGGESTION TO UBUNTU:
Set up the Grub loader to allow new installers to choose to:
1.  Stay with the suggested driver for their system;
2.  Choose a "generic" driver for their system (like a "safe mode" driver to at least let them get in).
3.  Choose a specific driver for their video board from a list of those compiled for Linux and included with the distribution.

If you are interested, I will include the modified Grub menu.lst in a subsequent post.

---

### Post by wallijonn on 2005-02-22
Good find. Can you please post your menu.lst?

---

### Post by Tyche on 2005-02-24
[QUOTE=wallijonn]Good find. Can you please post your menu.lst?[/QUOTE]

Per Your Request - the entire menu.lst

+++++++++++++++++++++++++++++++++++++++++++++++++

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
# foreground = 333333
# background = eeeeee
# color light-gray/blue black/light-gray

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,4)
kernel		/vmlinuz-2.6.8.1-3-386 root=/dev/hda6 ro quiet splash vga=791 screen=1024x768 xmodule=nv
initrd		/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.8.1-3-386 root=/dev/hda6 ro single splash vga=791 screen=1024x768 xmodule=nv
initrd		/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,4)
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1

++++++++++++++++++++++++++++++++++++++++++++++++++++++

Everything between the "plus marks" but not including them.  Good luck.

---

