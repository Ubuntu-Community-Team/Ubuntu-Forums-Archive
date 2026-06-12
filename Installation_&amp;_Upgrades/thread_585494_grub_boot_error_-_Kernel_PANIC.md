---
title: "grub boot error - Kernel PANIC"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by personal-data-removed on 2007-10-21
When i turn on the PC, i have this Grub menu:

Chainload into GRUB 2
[COLOR="Red"]Debian GNU/LINUX Kernel 2.6.22-14 Generic
Debian GNU/LINUX Kernel 2.6.22-14 (recovery mode)[/COLOR]
Debian GNU/LINUX Kernel 2.6.20-16 Generic
Debian GNU/LINUX Kernel 2.6.20-16 (recovery mode)
Debian GNU/LINUX Kernel 2.6.20-15 Generic
Debian GNU/LINUX Kernel 2.6.20-15 (recovery mode)
Other operative systems:
Windows XP

If i choose to start with kernel 2.6.22-14 (generic or recovery) it gives an error message: 

STARTING UP ...
[ 21.144483] Kernel Panic - not syncing
VFS: Unable to mount root FS on unk wh -block (0,0)

I can only start Ubuntu 7,10 kernel 2.6.22-14 by loading GRUB 2, it works without error, but GRUB 2, dont have Win XP boot option.

GRUB 2 (MENU)
Debian GNU/LINUX Kernel 2.6.22-16 Generic
Debian GNU/LINUX Kernel 2.6.22-16 (single user)
Debian GNU/LINUX Kernel 2.6.20-16 Generic
Debian GNU/LINUX Kernel 2.6.20-16 (single user)
Memory test (memtest 86+)

----------------------------------------------------------------------
I would like to fix the kernel panic error in Grub menu. 
How to fix ?

I alternative i would like to get rid of grub and replace with grub 2. 
Is possible to have only a simple boot option (Grub 2) with:

Debian GNU/LINUX Kernel 2.6.22-16 (Generic)
Debian GNU/LINUX Kernel 2.6.22-16 (single user)
Win xp boot
Mem test

I only can add Grub 2 menu on Grub 1 menu (chainload into).
Grub 2 doenst boot by itself, and dont have XP option.

Is possible ?, how to fix ? , how to improve my grub boot sequence ?
Thanks in advance.

Other bug:

I want the position of the bars on Ubuntu to be:
[ATTACH]47189[/ATTACH]

After reboot it always change to:
[ATTACH]47190[/ATTACH]
Very annoying.

How to fix ?

Thanks in advance


My Ubuntu menu.ist (could help)

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
# kopt=root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash locale=pt_PT

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
##      altoptions=(single-user) single
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

title		Chainload into GRUB 2
root		(hd1,0)
kernel		/boot/grub/core.img
savedefault

title		Debian GNU/Linux, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro quiet splash locale=pt_PT
savedefault

title		Debian GNU/Linux, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro single
savedefault

title		Debian GNU/Linux, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro quiet splash locale=pt_PT
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Debian GNU/Linux, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro single
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Debian GNU/Linux, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro quiet splash locale=pt_PT
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault

title		Debian GNU/Linux, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro single
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault

title		Debian GNU/Linux, kernel memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by personal-data-removed on 2007-10-21
I have added this 2 lines, but still getting the kernel panic error.
I can only mount the 2.6.22.-14 kernels with grub 2. How to use grub 2 as default ?

title		Debian GNU/Linux, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro quiet splash locale=pt_PT
[COLOR="Red"]initrd		/boot/initrd.img-2.6.22-14-generic[/COLOR]
savedefault

title		Debian GNU/Linux, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro single
[COLOR="Red"]initrd		/boot/initrd.img-2.6.22-14-generic[/COLOR]
savedefault

Also tryed to install again NVIDIA drivers.
ENVY was not working, so i uninstalled. Now i can not install envy again.
I still have nvidia driver working and nvidia config.
Envy dont work anymore in 7.10 , like Beryl ?

---

### Post by personal-data-removed on 2007-10-21
... err, managed to find a quick fix for the problem.

Added noapic nolapic nosplash to menu.ist, and kernel panic is gone.
I dont know if there is any loss of perfomance using this fix, any feedback welcome.

title		Debian GNU/Linux, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro quiet splash locale=pt_PT
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]noapic nolapic nosplash[/COLOR]
savedefault

title		Debian GNU/Linux, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d12e81b4-af7d-4769-8c08-a5a4af65c0ba ro single
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]noapic nolapic nosplash[/COLOR]
savedefault

[COLOR="Blue"]Still need help on bar error and Envy.
And in how to make Grub 2 the main kernel loader at boot.[/COLOR]

---

