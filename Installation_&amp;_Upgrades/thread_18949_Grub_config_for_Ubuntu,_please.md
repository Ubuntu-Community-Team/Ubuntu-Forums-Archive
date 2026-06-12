---
title: "Grub config for Ubuntu, please"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by maruchan on 2005-03-09
Installed Mepis and Grub but the installer forgot to put Ubuntu on the bootloader list. Anyone have the config information? I have Ubuntu on hda1.

Thanks!

---

### Post by alastair on 2005-03-09
Boot Mepis and mount Ubuntu (/dev/hda1) somewhere.

Then look at the grub config yourself - and add to the Mepis grub config?

---

### Post by Xian on 2005-03-09
[QUOTE=alastair]Then look at the grub config yourself - and add to the Mepis grub config?[/QUOTE]
Yeah, that's right. Mount your Ubuntu root partition while in Mepis and open the /boot/grub/menu.lst file with a text editor. Pull out the relevant bit and just add it as another option entry to your menu.lst for Mepis. It should appear on your next re-start.

---

### Post by maruchan on 2005-03-09
I tried this both ways, placing the Ubuntu text in the Mepis menu file, and placing the Mepis entries in the Ubuntu menu file and saving that over the Mepis one. Either way, Mepis still works, but the Ubuntu entries don't. They show up, though. It's just that when I press enter, it looks as if it's about to start and a couple lines of non-error text are displayed on the screen, but then it boots me back to the Grub menu.

Here is the current menu.lst file:

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
default  0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  10

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.8.1-5-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-5-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-5-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-5-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# Trying MEPIS entries.
title MEPIS at hdd1, kernel 2.6.10
kernel (hd1,0)/boot/vmlinuz-2.6.10 root=/dev/hdd1 nomce psmouse.proto=imps quiet splash=verbose vga=791 
initrd (hd1,0)/boot/initrd.splash 

# Trying MEPIS entries.
title MEPIS at hdd1, kernel 2.4.29
kernel (hd1,0)/boot/vmlinuz-2.4.29 root=/dev/hdd1 nomce quiet splash=verbose vga=791 hdc=ide-scsi 
initrd (hd1,0)/boot/initrd.splash 

```

Is there anything wrong with this that you can see? (especially with the Ubuntu entries)

---

### Post by Xian on 2005-03-09
[QUOTE=maruchan]I tried this both ways, placing the Ubuntu text in the Mepis menu file, and placing the Mepis entries in the Ubuntu menu file and saving that over the Mepis one. Either way, Mepis still works, but the Ubuntu entries don't. They show up, though. It's just that when I press enter, it looks as if it's about to start and a couple lines of non-error text are displayed on the screen, but then it boots me back to the Grub menu.[/QUOTE]
If you are booting with Mepis then you only need to edit that distro's menu.lst file. You can just leave the one in Ubuntu as it looks now. I would try to place the Ubuntu entry in your Mepis' menu.lst in the same format that it presently uses. For example, this:


title Ubuntu, kernel 2.6.8.1-5-686 
root(hd0,0)
kernel/boot/vmlinuz-2.6.8.1-5-686 root=/dev/hda1 ro quiet splash
initrd/boot/initrd.img-2.6.8.1-5-686
savedefault
boot

Becomes this:

# Trying Ubuntu entries.
title Ubuntu, kernel 2.6.8.1-5-686
kernel (hd0,0)/boot/vmlinuz-2.6.8.1-5-686 root=/dev/hda1 ro quiet splash
initrd (hd0,0)/boot/initrd.img-2.6.8.1-5-686

---

