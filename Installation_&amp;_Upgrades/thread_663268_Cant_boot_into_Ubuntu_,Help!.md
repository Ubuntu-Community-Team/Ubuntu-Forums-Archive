---
title: "Cant boot into Ubuntu ,Help!"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by grizzol on 2008-01-09
hey newbie here, jus installed ubuntu 7.10 (text base install) onto a thinkpad with xp pro, install went good and smooth but when it booted for the first time, grub only gave me this option:

Ubuntu 7.10, memtest86+
Other operating systems:
Windows NT/2000/XP (loader)

(in my other thinkpad grub gav me differnt options like a whole list of them like safe mode......etc, i dont know why on this laptop it only gave me these two options.)

,so i picked the Ubuntu option but all it does is run memtest forever.
i am just looking for a way to boot into ubuntu.  please help

tthanks

---

### Post by codesplice on 2008-01-09
Boot from the LiveCD, and navigate to your installed system.  Check out your /boot/grub/menu.lst file.  It should look *something* like mine:

```

title           Linux Mint, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

once you find that file, go on and post its contents so we can see what you're dealing with :)

---

### Post by grizzol on 2008-01-10
here you go , hope this helps, thanks again.

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
# kopt=root=UUID=0979f10b-02de-4058-92fb-4d4bf092c5b1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by logos34 on 2008-01-10
try this:
[B]
gksudo gedit /boot/grub/menu.lst[/B]

> ## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root	      (hd0,4)
kernel	     /boot/vmlinuz-2.6.22-14-generic root=UUID=0979f10b-02de-4058-92fb-4d4bf092c5b1 ro quiet splash
initrd	       /boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root	      (hd0,4)
kernel	     /boot/vmlinuz-2.6.22-14-generic root=UUID=0979f10b-02de-4058-92fb-4d4bf092c5b1 ro single
initrd	       /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by grizzol on 2008-01-10
so basically i just copy and replace that quote into the menu.lst???

---

### Post by logos34 on 2008-01-10
> **grizzol said:**
> so basically i just copy and replace that quote into the menu.lst???

yep

---

### Post by grizzol on 2008-01-10
so i booted into livecd went opened the menu file and typed in the changes but when i tried to save the file it said i had no permission doing it, so what next, btw thx for all the help

---

### Post by codesplice on 2008-01-10
You need root permissions to edit that file, so use sudo to open it:

```
sudo nano /boot/grub/menu.lst
```

or

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by grizzol on 2008-01-10
when trying th method i think it is not accessing the menu.lsst from the ubuntu partition instead it opens up the menu.lst from the livecd.  is there a way to open up the mnu.lst from the actual ubuntu . because wen i open the menu.lst it just opens up a blank document

---

### Post by logos34 on 2008-01-10
> **grizzol said:**
> when trying th method i think it is not accessing the menu.lsst from the ubuntu partition instead it opens up the menu.lst from the livecd.  is there a way to open up the mnu.lst from the actual ubuntu . because wen i open the menu.lst it just opens up a blank document

click on your root partition in Places>computer to mount it.  Look in the location bar and you will see it does so at /media/disk.  Then,

cd /media/disk
gksudo gedit /boot/grub/menu.lst

---

### Post by grizzol on 2008-01-10
did it but when booting up ubuntu it said file not found press any key to continue...

---

### Post by logos34 on 2008-01-10
Maybe the kernel images are not there in /boot (which would explain why only memtest was added to menu.lst). 

I recommend you reinstall.  It will take less time than troubleshooting.

---

### Post by grizzol on 2008-01-11
alright tried re installing but ur right always getting an error while  trying to install the kernel into thetarget system

---

### Post by logos34 on 2008-01-11
hmm...I'm thinking your iso is corrupted...possibly md5sum mismatch, or bad burn (maybe you burned it too fast, or the cd media is faulty, or it's the cd writer)

---

