---
title: "GRUB Error 29 when booting WinXPpro"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by PCT on 2005-11-08
Hello all!

Here's where I'm at.  I recently installed WinXPpro on the first half of my HDD with no problems.  Being new to Linux, and with this PC being a laptop, my friends recommended that I give Ubuntu a try.  Ubuntu 5.10 installed without a problem... GRUB also installed without a problem.  When I attempt to boot back into WinXPpro via GRUB, GRUB returns "Error 29: Disk write error".

Here's the result of "sudo fdisk -l" in a terminal window:

Disk /dev/hda: 20.0 GB, 20003880960 bytes
16 heads, 63 sectors/track, 38760 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19380     9767488+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2   *       19381       37900     9333765   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3           37900       38760      433755    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5           37900       38760      433723+  82  Linux swap / Solaris

Here's my menu.lst file contents.

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

What do I need to do to get WinXPpro to boot via GRUB?

TIA

---

### Post by Koybe on 2005-11-09
I don't know if it's the problem but I think your Windows partition should have the boot flag on.

---

### Post by linuxNewb on 2005-12-02
I am having the exact same issue (with windows xp home though). Does anyone know how to fix this. If it is the 'boot flag' as suggested above, how do you change that? Thanks.

---

### Post by elcu on 2006-01-06
I had the same problem.  In my case it was caused by the bootable flag being disabled on XP's partition.

- run 'sudo cfdisk <device>' (In my case, XP is installed on /dev/hda so <device> would be that)
- enable the bootable flag for the NTFS partition
- write changes
- quit
- reboot

Hopefully this fixes it for you.

---

