---
title: "Interrupted update, KDE &amp; Gnome not loading"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Adsrhodes on 2008-04-28
Hi,

I set my system up to update from 7.10 to 8.04 through the Update Manager. Happily went off to the pub, but when I got back, I found that the fuse had tripped for my house, and the installation had been interrupted. I could only get access to the command line. I re-started the update by entering:

[CENTER]sudo apt-get update && sudo apt-get dist-upgrade[/CENTER]

This completed the upgrade, but I now cannot get into KDE (which I was running on before) or Gnome (which I was hoping to return to. bring a bit bored with KDE)

At the GRUB screen, I am getting the option of:

[CENTER]Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)[/CENTER]

I choose that option, and a window pops up, telling me:

[CENTER]Ubuntu is running in low graphics mode[/CENTER]

I try to configure it, choosing by model (NVIDIA Geforce 8 series)

I then get a text-only screen saying:

[INDENT]Starting up...
Loading please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/d279c20e-29b8-45c6-6434-9d0cfe949492) = sda5(8,5)
kinit: trying to resume from (/dev/disk/by-uuid/d279c20e-29b8-45c6-6434-9d0cfe949492)
kinit: no resume image, doing normal boot...

Ubuntu 8.04 adam-desktop tty1

adam-desktop login:[/INDENT]

I am tempted to try a totally new install, but I don't have my sda1 drive backed up (foolish, I know).

Anyone any advice?

---

### Post by russ18uk on 2008-04-28
Got access to the net using the CLI? Try and reinstall Gnome. Don't know the exact command, apt-get install gnome or apt-get install desktop-gnome... you should probably uninstall it as well. As well, but it seems like your grub didn't configure properly either; you'd need to boot to the lines linking to your 8.04 install rather than your old install which the kernel has probably been removed. Again, I'm not learned enough in these areas to know how to resolve them, just my 2c :)

Good luck.

---

### Post by Adsrhodes on 2008-04-28
Awesome, that did the trick. I had a little trouble with the resolution, but reconfigured xconfig, and it is all new and shiny!

GRUB is still adamant that I am on 7.10, but to be honest, I can live with that as long as it all loads and works fine! I think I will get rid of the dual boot anyway, so I won't ever see GRUB.

Thanks again!

---

### Post by PmDematagoda on 2008-04-28
Actually, I don't think you may be going the right way here by using the Gutsy kernel instead of the Hardy one, could you post the output of:-
```
cat /boor/grub/menu.lst
```
But if you don't want to use the new kernel, that's ok, but it is risky and some dependency or security issues may pop-up later on.

---

### Post by Adsrhodes on 2008-04-28
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
timeout		3

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
# kopt=root=UUID=6b00d588-d646-4b02-9e34-9d0905733eed ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6b00d588-d646-4b02-9e34-9d0905733eed ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6b00d588-d646-4b02-9e34-9d0905733eed ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6b00d588-d646-4b02-9e34-9d0905733eed ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6b00d588-d646-4b02-9e34-9d0905733eed ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

