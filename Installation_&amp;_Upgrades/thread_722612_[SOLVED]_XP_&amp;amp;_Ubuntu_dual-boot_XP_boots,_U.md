---
title: "[SOLVED] XP &amp;amp; Ubuntu dual-boot: XP boots, Ubuntu sez &amp;quot;Error 22&amp;quot;"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by zoopzoop on 2008-03-12
I just thought I had my dual-boot setup up and running and then I reboot and when I select Ubuntu in Grub I get a nonchalant

```
Error 22: no such partition
```

Booting into Win XP works fine!

These are my partitions:

On /dev/hda:
/dev/hda1 - ntfs - Data

On /dev/sda:
/dev/sda1 - ntfs - Win XP
/dev/sda4 - ext3 - Ubuntu home
/dev/sda3 - ext3 - Ubuntu
/dev/sda2 - linux-swap

This is my /boot/grub/menu.lst:

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
color cyan/blue white/blue

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
# kopt=root=UUID=97f59032-5fca-42dc-9ef2-88a853c66b50 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
# defoptions=quiet splash vga=773

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
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97f59032-5fca-42dc-9ef2-88a853c66b50 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97f59032-5fca-42dc-9ef2-88a853c66b50 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Microsoft Windows XP Professional
#root		(hd1,0)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1
```

I tried setting "root" for Ubuntu (first entry) to "(hd1,1)", "(hd1,0)", "(hd1,3)", to no avail.

And my /boot/grub/device.map

```
(hd0)	/dev/hda
(hd1)	/dev/sda
```

Now I suspected that it might have something to do with which partition has the boot flag (my Win XP partition has) and tried setting this to the Ubuntu partition, but still the same, Win XP works fine, Ubuntu won't boot.

I'm thankful for every idea / comment!

---

### Post by Pumalite on 2008-03-12
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by zoopzoop on 2008-03-12
Thanks, Pumalite.
I wanted to leave reinstalling Grub as the last option.

Does anyone have another idea what could be the problem?

---

### Post by sillyxone on 2008-03-12
try the other combinations such as (hd0, 2)

I'm not sure what might be wrong but since XP is listed in (hd0, 0) and boot up fine, Ubuntu in sda3 should be (hd0, 2) logically :-)

---

### Post by logos34 on 2008-03-13
yeah, I think all you need to do is change **groot** and **root** lines in menu.lst to (hd**0**,2), because sda is your boot disk.  Wouldn't hurt to edit device.map either.

---

### Post by zoopzoop on 2008-03-13
Success!
I changed to (hd0,2) and it worked.

Some questions arise:

WHY does it work?
As you see in my device.map, hd0 is my /dev/hda drive that does not contain any OS.
The thing I did in between was uncommenting the last lines of my menu.lst

```
#title		Microsoft Windows XP Professional
#root		(hd1,0)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1
```

and boot Win XP from that entry, which worked fine.
Could it be that the "map" entries have something to do with it?
Perhaps for some reason hd0 and hd1 were **permanently** swapped?

Also, what would change if I uncomment the groot line (and change it to hd(0,2)), as logos34 suggested?

And, lastly, logos34, what do you mean by "Wouldn't hurt to edit device.map either."?
I'd rather not touch it to not mess things up even more, just if it is necessary.

I'd be thankful for any clarification.

---

### Post by logos34 on 2008-03-13
(hd0,2) works because sda is your boot disk/first in Bios hard disk boot order (i.e. hd0).  The device.map doesn't really matter except sometime for the map commands and windows.  I just suggested you change it for consistency's sake.

But you're saying you can boot windows with the above entry when you uncomment it? How I don't know, because windows boot partition is on the same drive as ubuntu--(hd0,0) should work, WITHOUT the map commands.  Correct device.map, take out the map lines in xp entry above, and try booting xp again at (hd0,0)--that's what *should* work.

---

### Post by zoopzoop on 2008-03-14
Thanks, logos34, everything works fine now!

---

