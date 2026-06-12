---
title: "Grub error"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by colofnature on 2008-09-22
I just installed Ubuntu on an old spare HD I had lying around and now I have a problem booting. When I allow the PC to boot to the first hard drive the grub menu appears and everything works fine - except that I didn't install Ubuntu on that drive and as this is a shared PC I'd rather it booted direct to Windows unless I hit F8 and select the alternate drive. When I do this and choose Ubuntu from the list I get "Error 17: Cannot mount selected partition"

I've searched the forum, but I'm kind of new to linux so it's all gobbledegook to me. What I want to know is:
1. Can I make my Windows drive default to booting Windows without showing the list? and
2. How do I fix the error with grub when I boot to the second drive?

I suppose these will help:
sudo fdisk -l:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x009a0099

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244197184+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf520fedb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

```

and \boot\grub\menu.lst:
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
# kopt=root=UUID=95840faf-a33d-463c-af5d-20dcee12a7ea ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=95840faf-a33d-463c-af5d-20dcee12a7ea ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=95840faf-a33d-463c-af5d-20dcee12a7ea ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1

```

Any help would be appreciated, I'm probably not going to be able to sleep tonight until I get this sorted!

Cheers, Col

---

### Post by Pumalite on 2008-09-22
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
You probably have a mix of SATA and IDE.
Check this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by colofnature on 2008-09-22
Maybe I'm being thick, but I don't get it...

I have Windows installed on a SATA drive and Ubuntu on an IDE drive. I want Windows to be the first boot disk, so I set the BIOS up that way. So far so good. When I do nothing I want Windows to boot automatically without going into the grub menu - I didn't want grub to interfere with the Windows drive at all. Instead, when the SATA drive boots I get the grub menu, which is no good.

Then, if Windows behaves correctly, I should have to hit F8 and choose to boot from the IDE drive. If I do so, I'm presented with the grub menu, which is fine, but when I try to load Ubuntu, or let it time out, I get the error.

Can someone please explain the problem to me - in simple words :) How do I get rid of grub from the SATA drive, and how do I get grub to work on the IDE drive? :confused:

---

### Post by Pumalite on 2008-09-22
You can restore your Windows MBR and later boot Ubuntu with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
But if I were you I would take a good look at the link I gave and learn to fix your installation using Grub.

---

### Post by cariboo on 2008-09-22
Why not set windows as the default boot in grub, the cut the wait time to zero:

Set

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		3
```

This will now boot Vista by default

Now set the wait time:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

```

You will still be able to get to the menu by pressing Esc

Jim

---

### Post by colofnature on 2008-09-22
Okay, I changed the references to hd0 to be hd1, and vice versa, and that's fixed it. Should I also change the groot to be hd0 as well?

Thanks for the pointers Pumalite, and you're right: it's better to fix it oneself than to be told what to do. But having said that, it's 3:45am so you can't blame me for being lazy! :)

---

### Post by Pumalite on 2008-09-22
All you have to do is edit menu.lst and add below the AUTOMAGIK line an entry for Windows:
title		Windows 
root		(hd0,0)
makeactive
chainloader	+1
If it doesn't work; make 'root' (hd1,0)

---

### Post by lswb on 2008-09-22
It appears that you installed grub to the mbr of sda1. When you installed ubuntu was the 250GB drive the boot drive? If so than what happened (and actually this would be the expected behaviour IMO) Is that grub was installed in the boot sector of the 250 GB drive so that it would load at boot and show you the menu. There are a few things you can do:

My choice would be to leave grub as it is and just edit the menu.lst file for a short timeout, hidden display, and default boot to Windows. To do this with the menu.list you posted, open it as root ("gksudo gedit /boot/grub/menu.lst" is one way, make a backup copy 1st) and change these lines:

default 0
to
default 3

timeout 10
to 
timeout 3
(that's what I use anyway)

#hiddenmenu
to 
hiddenmenu

The comments in the menu.lst file explain what these changes do. I would recommend this method as it hides most of what you want to hide without having to fool with the bios settings to select the OS you want to boot.

If you really want to use the BIOS to switch boot drives then you will have to 

1)install grub to the MBR of the 80GB drive: 

2)restore the MBR of the 250GB to whatever windows expects.

If you decide to go that way and need help post again, It's been a while since I've used those grub commands and I'm hesitant to post them here from memory.

---

### Post by Pumalite on 2008-09-22
> **colofnature said:**
> Okay, I changed the references to hd0 to be hd1, and vice versa, and that's fixed it. Should I also change the groot to be hd0 as well?



Thanks for the pointers Pumalite, and you're right: it's better to fix it oneself than to be told what to do. But having said that, it's 3:45am so you can't blame me for being lazy! :)

Change 'groot' too. Have a good night's rest.

---

