---
title: "[SOLVED] Unrecognized device error"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by arthurbr on 2008-08-15
Hi,
I'm using GRUB = dualboot with two HD (one with Ubuntu, the other WinXP)
After upgrading to the 2.6.24-21 kernel, I got an error booting Ubuntu, but started after editing the first line and changed hd(1,0) to hd(0,0) ( as usual after an upgrade)
Then edited menu.lst and changed hd(1,0) to hd(0,0) for each kernel.
After rebooting got Error 11 : unrecognized device error while trying to boot Ubuntu
(BTW booting on XP works fine)
This is my menu.lst file
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
# kopt=root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-21-386

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-20-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-20-386

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-18-386

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-17-386

title		Ubuntu 8.04.1, kernel 2.6.24-16-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-16-386

title		Ubuntu 8.04.1, memtest86+
root		hd(0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader     +1

```
Does anybody have a suggestion?
Much appreciated

---

### Post by arthurbr on 2008-08-15
Replaced hd(0,0) with (hd0,0) and it worked

---

### Post by iaculallad on 2008-08-15
> **arthurbr said:**
> Hi,
I'm using GRUB = dualboot with two HD (one with Ubuntu, the other WinXP)
After upgrading to the 2.6.24-21 kernel, I got an error booting Ubuntu, but started after editing the first line and changed hd(1,0) to hd(0,0) ( as usual after an upgrade)
Then edited menu.lst and changed hd(1,0) to hd(0,0) for each kernel.
After rebooting got Error 11 : unrecognized device error while trying to boot Ubuntu
(BTW booting on XP works fine)
This is my menu.lst file
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
# kopt=root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-21-386

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-20-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-20-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-20-386

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-18-386

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-17-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-17-386

title		Ubuntu 8.04.1, kernel 2.6.24-16-386
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-386 (recovery mode)
root		hd(0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=9606c1bd-744c-425d-8665-166a1084ad5a ro single
initrd		/boot/initrd.img-2.6.24-16-386

title		Ubuntu 8.04.1, memtest86+
root		hd(0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader     +1

```
Does anybody have a suggestion?
Much appreciated

The correct way of marking your thread as "SOLVED" is to use the THREAD TOOLS located at the upper right-hand corner of your message. Just above the window of your message. Mark it as "Mark this thread as Solved".

---

### Post by arthurbr on 2008-08-15
Thx iaculallad, corrected the mistake

---

