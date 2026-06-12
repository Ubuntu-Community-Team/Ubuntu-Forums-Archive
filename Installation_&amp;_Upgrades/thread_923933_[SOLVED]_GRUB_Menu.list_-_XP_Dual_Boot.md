---
title: "[SOLVED] GRUB Menu.list - XP Dual Boot"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by OneRingShort on 2008-09-18
Hello everyone!

I ran into a problem with GRUB, and I'm out of ideas.  I've spent the day searching around for answers, but I couldn't seem to find one that worked.

What's happening:

I did a clean install of Windows XP on a 75g partition on one of my hard drives.  I then ran an install of Ubuntu Hardy usuing the manual install option to configure the partitions.  I put Ubuntu and the swap on the same disk as Windows (separate partitions), and had the entire second hard drive for the /home.

After I tried to boot back into windows, I realized that Windows wasn't in the GRUB boot loader menu.  I went into Ubuntu, checked the /boot/grub/menu.lst and found there wasn't an entry for Windows (I thought Ubuntu automatically detected other operating systems on install?).  Here is the menu.lst contents:

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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=e9e02207-cd94-43b0-9ce1-a0f32cfc2718 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e9e02207-cd94-43b0-9ce1-a0f32cfc2718 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e9e02207-cd94-43b0-9ce1-a0f32cfc2718 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e9e02207-cd94-43b0-9ce1-a0f32cfc2718 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e9e02207-cd94-43b0-9ce1-a0f32cfc2718 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I tried putting an entry for it as per the template in the comments section, but I got the result "NTLDR is missing".  I tried several other configurations recommended at various websites, and I would get the "Error 13: Invalid or unsupported executable format" message.  So after no avail, I just restored the menu.lst back to the original (above).

Do you know what entry needs to be entered?

**Additional information:**
-Both hard drives are SATA
-sda1: Windows XP
-sda2: Swap
-sda3: Ubuntu Root /
-sdb1: Ubuntu Home /home

I think that should about cover it.  If you need anymore information, please let me know.

Thanks for your time,

Matt

---

### Post by aragorn2909 on 2008-09-18
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

This is what mine looks like.  Hope it helps.  (just change the title line to reflect your XP install)

---

### Post by OneRingShort on 2008-09-18
Thanks for the quick response, but unfortunately it didn't do the trick.  I tried putting that one in, rebooted and got the following message:

```
NTLDR is missing
Press Control+Alt+Delete to restart
```

---

### Post by unutbu on 2008-09-18
Sometimes Windows installs the NTLDR file in a partition other than the main Windows OS partition. In such situations, the Ubuntu installer may overwrite the NTLDR if it was directed to install itself into that partition.

If that sounds like your situation, you can restore your NTLDR by using the instructions found here:
[http://ubuntuforums.org/showthread.php?p=5082723#post5082723](http://ubuntuforums.org/showthread.php?p=5082723#post5082723)

---

### Post by aragorn2909 on 2008-09-18
> **OneRingShort said:**
> Thanks for the quick response, but unfortunately it didn't do the trick.  I tried putting that one in, rebooted and got the following message:

```
NTLDR is missing
Press Control+Alt+Delete to restart
```

An all too common problem.

There are some good resources online.  Try [here]("http://www.computerhope.com/issues/ch000465.htm").

I'm sorry I can't help further with that one.

---

### Post by OneRingShort on 2008-09-18
> **unutbu said:**
> Sometimes Windows installs the NTLDR file in a partition other than the main Windows OS partition. In such situations, the Ubuntu installer may overwrite the NTLDR if it was directed to install itself into that partition.

If that sounds like your situation, you can restore your NTLDR by using the instructions found here:
[http://ubuntuforums.org/showthread.php?p=5082723#post5082723](http://ubuntuforums.org/showthread.php?p=5082723#post5082723)

Wonderful, that did the trick.  Thank you for providing a direct link, definitely made things easier.

On another note:  This is what I love about the Ubuntu/Linux community...you have a problem, write a thread, and it's solved in an hour!  I don't think I've ever seen a forum as active as this one.  I don't think anyone would solve a problem like this with Windows nearly as fast with Microsoft tech support.
=D>

Matt

---

