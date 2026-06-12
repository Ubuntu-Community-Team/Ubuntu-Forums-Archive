---
title: "[SOLVED] Dual Boot Grub Problem"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by cyberia81 on 2007-12-24
Hello. I recently set up my fiance&#347; computer to dual boot XP and Ubuntu with two hard drives. Everything was set up and working just fine until today. He restarted the computer and XP disappeared from Grub.

I have scoured the forums and read many different threads/posts, but nothing I try has resolved the problem.

This is what I have done so far:

1- Tried Super Grub disk.
2- Modified menu.lst per instructions on the forum.
3- Somehow I managed to change menu.lst so that now XP is the only thing to boot. I can see the Ubuntu drive when I boot with an Ubuntu Live CD.

This is what I have done, and unfortunately I am pretty sure it is wrong:

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


title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
#
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=01fbbed3-3845-4038-a9ee-add5b7a20b50 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=01fbbed3-3845-4038-a9ee-add5b7a20b50 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
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
# kopt=root=UUID=01fbbed3-3845-4038-a9ee-add5b7a20b50 ro

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



### END DEBIAN AUTOMAGIC KERNELS LIST
```

Any help would be greatly appreciated. It has been a long day, so I do not remember everything I tried. If you need more information please let me know. Thank you!

---

### Post by logos34 on 2007-12-24
> "[The ### END DEBIAN AUTOMAGIC KERNELS LIST sign] marks the end of the automagic kernels list. Above this sign, there should be no entries placed for strange operating systems, or they will be automagically removed next time there is a kernel update."

[http://users.bigpond.net.au/hermanzone/p15.htm#ubuntu_OS_entry](http://users.bigpond.net.au/hermanzone/p15.htm#ubuntu_OS_entry)

Your menu.lst should look like this:
> 
**## ## End Default Options ##**

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=01fbbed3-3845-4038-a9ee-add5b7a20b50 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=01fbbed3-3845-4038-a9ee-add5b7a20b50 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

**### END DEBIAN AUTOMAGIC KERNELS LIST**

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1


---

### Post by logos34 on 2007-12-24
oh, and comment out (put a # mark in front of) **hiddenmenu** option unless you do not want to see the menu at boot

---

### Post by transporter_ii on 2007-12-24
Sorry if I missed this in someone else's reply, but you might want to make a backup of your grub menu.lst as well. I spent all afternoon getting a dual boot system to work. I had it working fine, too, and then I upgraded everything and I guess something writes over the menu.lst file with a default file, because my Windows Vista menu item just totally vanished and I had to waste time figuring it out all over again. 

Transporter_ii

---

### Post by cyberia81 on 2007-12-24
Thank you so much! Everything is back to normal. I'm pretty embarrassed because it was such an easy fix and it makes perfect sense now, but I'm still very new to this. Thanks again for the help and your prompt reply! 

Thank you for the advice about backing up the file. The first time I did it I created a backup but that was somehow altered as well. I emailed it to myself this time. :)

Happy Holidays!

---

### Post by logos34 on 2007-12-24
> **cyberia81 said:**
> Thank you so much! Everything is back to normal. I'm pretty embarrassed because it was such an easy fix and it makes perfect sense now, but I'm still very new to this. Thanks again for the help and your prompt reply! 

Thank you for the advice about backing up the file. The first time I did it I created a backup but that was somehow altered as well. I emailed it to myself this time. :)

Happy Holidays!

You quite welcome!  Lots of people do what you did, it's a common mistake...often they put it at the top because they want it listed first on the menu.lst.  Then a kernel update comes along and poof! windows entry is gone.

Happy holidays to you too!

---

