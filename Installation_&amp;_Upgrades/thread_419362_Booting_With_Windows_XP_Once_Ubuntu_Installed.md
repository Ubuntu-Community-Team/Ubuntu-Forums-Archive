---
title: "Booting With Windows XP Once Ubuntu Installed"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Sevigny86 on 2007-04-22
Hi, I'm new to Linux and therefore my knowledge in dualbooting is null. I just bought a new HD and wanted to organize my files with the new space. Thus I reformatted my two prior HDs. My main goal was to keep my smallest for OSs and so when I reformatted the HD I installed Windows XP, followed by Ubuntu on the same disk. However now when I try to boot and enter Windows XP, GRUB doesn't allow the selection for Windows. Therefore my question is what do I do to boot into Windows? Can I fix this or do I have to reinstall Windows?

Thanks in advance for the advice!

---

### Post by Martje_001 on 2007-04-23
Can you post your GRUB config file?

ALT+F2 --> gedit /boot/grub/menu.lst

---

### Post by Sevigny86 on 2007-04-23
Not sure if this is what you wanted to see, but this is what I got when I did as you said. Thanks in advance for any help!

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
# kopt=root=UUID=16c7e292-5427-4541-8392-44d5e9417e42 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=16c7e292-5427-4541-8392-44d5e9417e42 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=16c7e292-5427-4541-8392-44d5e9417e42 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Martje_001 on 2007-04-23
You have to add this on the very last lines:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
By (hd0,0) you have to fill in your hard disk and you partition. Begin to count with zero!
If you have Windows installed on you 3rd hard disk second partion it becomes: (hd2,1), got it?

---

### Post by Sevigny86 on 2007-04-23
Thank you for the help. However when I try to edit, it says it is write only and I cannot edit the file... what should I do with this?

---

### Post by icechen1 on 2007-04-23
> **Sevigny86 said:**
> Thank you for the help. However when I try to edit, it says it is write only and I cannot edit the file... what should I do with this?

use sudo gedit [path to your grub config file here]
and tape your password

---

### Post by icechen1 on 2007-04-23
> **icechen1 said:**
> use sudo gedit [path to your grub config file here]
and tape your password

ok it is ```
sudo gedit /boot/grub/menu.lst
``` tape that in the terminal

---

### Post by Sevigny86 on 2007-04-23
Damn well I can edit the menu.lst, however when I boot it doesn't work :S Is it possible that Ubuntu damaged or maybe even replaced my Windows boot sector since I installed both on the same HD without partitioning it?

---

### Post by Martje_001 on 2007-04-24
Did you erase the whole disk? Yes, then Windows is lost. But maby not, can you send a screenshot of gparted?

You install it by tape in a terminal:
```
sudo apt-get install gparted
```

---

### Post by Sevigny86 on 2007-04-25
Hey well I just want to thank you for the help, but I succumbed to the alternate method... Figured I was wasting more time trying to fix than to reformat and reinstall so I was smart about it this time and partitioned my disk, lol. Anywho, thanks for the input I really appreciate it!

---

