---
title: "can't boot, won't boot - installtion arrrgh x many"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by joey-elijah on 2008-09-28
I seem to have 'upgraded' by wubi installation o0nto my vista disk. hmm. Never mind losing vista, but i have a boot predicament upon every boot now.

On a boot up I'm presented with

UBUNTU
UBUNTU (rfecovery)
UBUNTU (mem test)
OTHER OPERATING SYSTEMS
VISTA/LONGHORN LOADER
UNBOOTIN-PARTITION MANAGER
OTHER OPERATING SYSTEMS
WINDOWS

no matter which i click, i'm greeted either by

error 13 - invalid or unsupported executable format

or

error 17 - cannot mount selected partition

Lush.

I can, however, boot into Linux but editing the first Ubuntu command and changing the (0,0) bit of the command, except i have to change it EVERYTIME. if on last boot it was (0,0) i have to change it to (1,0) to boot up, or i get error 17. And vice versa, if it was (1,0) last boot, needs to be (0,0).

Now obviously I'm grateful i can boot at all, but having lost vista and having to manually muck about to get into Ubuntu, I'm getting narked.

Cny help? I'm a bit novice-esque - mainly used to wearing my sudo apt-get'n boots....

I have two internal harddrives, with Ubuntu writing over vista which was on an 80gb drive - set to boot first i think. and the wubi was originally on a 160gb drive, which now hosts grub, i think... hrrrmph.

any help will be met with marriage proposals, spare livers, you name it!

---

### Post by mikewhatever on 2008-09-28
Boot Ubuntu again, then open Applications->Accessories->Terminal and copy the following two commands one by one, hitting Enter under each:
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
gksudo gedit /boot/grub/menu.lst

The second one will open Grub's config file for editing, find the entry you want to change, edit, save and exit.

---

### Post by joey-elijah on 2008-09-29
> **mikewhatever said:**
> Boot Ubuntu again, then open Applications->Accessories->Terminal and copy the following two commands one by one, hitting Enter under each:


The second one will open Grub's config file for editing, find the entry you want to change, edit, save and exit.

i've tried this before and it gave me a grub "failed to load" error so i one live cd and correcting it all later, i could manipulate ubuntu to start again. 

if i change the "grub" to (1,0)* or whatever i've used to load ubuntu, i get a grub fail to laods error. it doesn't matter which i change it to. Strange? 

I'll post my grubmenu in case it's a  simple case i have no idea to look at:

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
timeout 	10

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
# kopt=root=UUID=08417625-7107-48f0-a27c-e4b1e4f2e737 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=08417625-7107-48f0-a27c-e4b1e4f2e737  ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=08417625-7107-48f0-a27c-e4b1e4f2e737  ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


title UNetbootin-partitionmanagerrev146
   root (hd1,0)
   kernel /ubuntu/disks/boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram
   initrd /ubuntu/disks/boot/ubninit
   boot


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,0)
makeactive
chainloader +1
boot

```

---

### Post by mikewhatever on 2008-10-02
Here is a similar post. [http://ubuntuforums.org/showthread.php?t=931982](http://ubuntuforums.org/showthread.php?t=931982)
I've never used wubi myself, but according to the link above, (hd1,0) line shouldn't be there at all.

---

### Post by joey-elijah on 2008-10-04
thanks, i managed to sort it out with the power of a live cd, some intuition and a helpful post, but thanks anyway! will bookmark incase i ever need to use it!

---

