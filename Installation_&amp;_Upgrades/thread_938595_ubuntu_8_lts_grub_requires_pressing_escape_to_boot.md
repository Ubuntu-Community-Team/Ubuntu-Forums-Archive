---
title: "ubuntu 8 lts grub requires pressing escape to boot?"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by opt1k on 2008-10-05
Hi All.
Quick question, fresh install of ubuntu on a laptop. It is requiring me to press escape at the grub loading screen after it says 2 to load ubuntu otherwise the system just hangs ntil escape is pressed to go into the menu.

I figure there is a simple solution to this. Any ideas?
This laptop has ONLY ubuntu on it. and it is a fresh install. It did this from the moment the install was completed.

---

### Post by Eto_Demerzel on 2008-10-05
Could you post the contents of the file /boot/grub/menu.lst?

---

### Post by cariboo on 2008-10-05
How long have you got the boot delay set for in grub?

Usually you only need to hit esc to see the menu, then choose the os you want to load and hit return. I have my delay set for 5 seconds as I triple boot this system, on my server it is set to zero as hardy is the only os on it.

Like the previous poster said please post youe /boot/grub/menu.lst file.

Jim

---

### Post by opt1k on 2008-10-05
~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=929827d7-d368-4abc-84b5-9d137e4ac500 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=929827d7-d368-4abc-84b5-9d137e4ac500 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=929827d7-d368-4abc-84b5-9d137e4ac500 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by xreaper on 2008-10-05
theres always an alternative solution. install start up manager:

sudo apt-get install startupmanager

Its basically a program that can help you sort out your start up. You can use it to go directly to the boot menu, and wait 1 second before booting ubuntu if thats what you want.

---

### Post by Eto_Demerzel on 2008-10-05
Hmmm... I don't know why your system hangs till you press escape. But comment out the word hiddenmenu.

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Blue"]#hiddenmenu[/COLOR]
```

Now startup and see what happens.

---

