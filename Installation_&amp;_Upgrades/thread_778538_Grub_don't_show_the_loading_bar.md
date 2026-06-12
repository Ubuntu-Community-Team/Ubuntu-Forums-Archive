---
title: "Grub don't show the loading bar"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by EreboShade on 2008-05-02
So recently, I upgrade Ubuntu 7.10 in 8.04 on my pc. I just search but i don't see a solution.
During startup, loading bar is going back and forth and then before loading that go only forth, i see only the loading words with [OK] until it shows the login screen.

How can i see only the loading bar during loading without the words with [OK]?

:popcorn:

i have installed start-up manager, i changed the resolution but i see it, too. with Ubuntu 7.10 there aren't problems!
this is my grub file

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

## password 
# .... (for privacy in forum i delete this tag)

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
# kopt=root=UUID=9d71e6e5-3552-41e4-b6b0-bef268cb2463 ro

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
# defoptions=locale=it_IT vga=795 quiet splash

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9d71e6e5-3552-41e4-b6b0-bef268cb2463 ro locale=it_IT vga=795 quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9d71e6e5-3552-41e4-b6b0-bef268cb2463 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9d71e6e5-3552-41e4-b6b0-bef268cb2463 ro locale=it_IT vga=795 quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9d71e6e5-3552-41e4-b6b0-bef268cb2463 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9d71e6e5-3552-41e4-b6b0-bef268cb2463 ro locale=it_IT vga=795 quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9d71e6e5-3552-41e4-b6b0-bef268cb2463 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
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
```

---

### Post by EreboShade on 2008-05-02
up

---

### Post by EreboShade on 2008-05-02
up

---

### Post by EreboShade on 2008-05-03
up O_O

---

### Post by EreboShade on 2008-05-03
up

---

### Post by dstew on 2008-05-03
Hi EreboShade. The only guess I have is to remove the word quiet from the menu.lst item. See if this helps. The kernel options **quiet splash** you should leave alone, this should make the splash screen start (orange bar going forward). Maybe the second quiet removes it.```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9d71e6e5-3552-41e4-b6b0-bef268cb2463 ro locale=it_IT vga=795 quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
[COLOR="Red"]quiet[/COLOR]
```Remove the red [COLOR="Red"]quiet[/COLOR].

The other possible problem is the vga=795 kernel option. Maybe this mode doesn't work with the splash screen. What happens if you remove this?

---

### Post by Max_Kbrown on 2008-06-03
Same problem here but in my situation it started after I installed PClinuxOS 2007 (dual boot). I've installed other distros on that same partition and didn't have this problem. I tried the solutions mentioned above but no luck, still looking for a solution to this nuisance.

---

### Post by pjalegria on 2008-11-04
+1:lolflag:

---

