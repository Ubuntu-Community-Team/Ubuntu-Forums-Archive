---
title: "Installed OpenSuse with GRUB. ubuntu wont load"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by dummyhead3 on 2008-10-15
I have recently decided to try out something other than Ubuntu, so I decided to give OpenSUSE a try. I also have Windows Vista on my hard drive.
I partitioned my HD using the ubuntu Live Cd and setup my HD as follows:

sda1: Windows Recovery
sda2: Windows Vista
sda3: Ubuntu
sda4: Exteded partition containing:
      sda5: OpenSUSE
      sda6: swap (for both Ubuntu and OpenSUSE)

This is the menu.lst on OpenSUSE:

```
# Modified by YaST2. Last modification on Wed Oct 15 19:53:40 EDT 2008
default 0
timeout 8
gfxmenu (hd0,4)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0
    root (hd0,4)
    kernel /boot/vmlinuz-2.6.25.16-0.1-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDS7216_PVC301Z2UNHGPJ-part5    resume=/dev/sda6 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.25.16-0.1-default

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 8.04.1, kernel 2.6.24-21-generic (/dev/sda3)###
title  Ubuntu 8.04.1, kernel 2.6.24-21-generic (/dev/sda3)
    rootnoverify (hd0,2)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,4)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,4)
    chainloader (hd0,1)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0
    root (hd0,4)
    kernel /boot/vmlinuz-2.6.25.16-0.1-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDS7216_PVC301Z2UNHGPJ-part5 showopts ide=nodma apm=off acpi=off noresume edd=off  x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.25.16-0.1-default

###Don't change this comment - YaST2 identifier: Original name: Kernel-2.6.25.16-0.1-default###
title Kernel-2.6.25.16-0.1-default
    root (hd0,4)
    kernel /boot/vmlinuz-2.6.25.16-0.1-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDS7216_PVC301Z2UNHGPJ-part5    resume=/dev/sda6 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.25.16-0.1-default

```

Baisically I trying to chainload the ubuntu GRUB, but it giving me an error

Also, this is the menu.lst on my ubuntu partition: 

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

# the Simple_Green can be replaced by another theme
gfxmenu /boot/grub/message.Simple_Green 

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8b6907f7-323e-4c7f-b483-dada1b001a97 ro

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
# defoptions=vga=758 splash

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=8b6907f7-323e-4c7f-b483-dada1b001a97 ro vga=769 splash quiet
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=8b6907f7-323e-4c7f-b483-dada1b001a97 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8b6907f7-323e-4c7f-b483-dada1b001a97 ro vga=769 splash quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8b6907f7-323e-4c7f-b483-dada1b001a97 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Also, I booted Ubuntu once, but then it stopped booting. Windows boots perfectly.

---

### Post by dummyhead3 on 2008-10-15
By the way, the error I et is error 18 when i try to chainload the ubuntu GRUB:
<CODE>rootnoverify (hd0,2)
chainload +1

GRUB

GRUB loading, please wait...
Error 18</CODE>

---

### Post by caljohnsmith on 2008-10-15
To chainload Grub from your Ubuntu partition, you have to install Grub to the boot sector of the Ubuntu partition. But an easy way to accomplish basically the same thing is to just put the following in your OpenSUSE's menu.lst:
```
title Ubuntu Grub Menu
configfile (hd0,2)/boot/grub/menu.lst
```
Give that a shot and let me know how it goes. :)

---

### Post by dummyhead3 on 2008-10-15
Great, thanks!
I'm in ubuntu now, so do I keep the Grub the way it is, or do i change it back to the chainload +1?
Also, for some reason Grub couldn't find my theme but that's unimportant.
Thanks again.

---

### Post by caljohnsmith on 2008-10-15
> **dummyhead3 said:**
> Great, thanks!
I'm in ubuntu now, so do I keep the Grub the way it is, or do i change it back to the chainload +1?
Also, for some reason Grub couldn't find my theme but that's unimportant.
Thanks again.
Well the only way you can use the "chainload +1" notation is if you install Grub to the boot sector of your Ubuntu partition, but the above method of using "configfile" accomplishes the same end result. In case you want to experiment though, the following will install Grub to the Ubuntu partition boot sector:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0,2)
grub> quit
```
After that you should be able to use the chainloader notation that you tried before. :)

---

### Post by dummyhead3 on 2008-10-16
Ok, thnx, I'll try that some time when I feel like screwing around with my system again!

---

