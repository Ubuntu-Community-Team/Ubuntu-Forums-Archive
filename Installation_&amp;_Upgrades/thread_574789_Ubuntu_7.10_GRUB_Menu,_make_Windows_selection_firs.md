---
title: "Ubuntu 7.10 GRUB Menu, make Windows selection first"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by TheChaosTheory89 on 2007-10-13
Okay, I am using Ubuntu 7.10 with Windows XP

When I turned it on, I can see the GRUB menu with Windows XP and Ubuntu, but the highlight was selected on Ubuntu, how do I make it select on the Windows XP and let it boot by auto timer???

---

### Post by taurus on 2007-10-13
You need to change the "default" setting in /boot/grub/menu.lst from Ubuntu to XP.  Remember,  each **title** counts as one and you start counting from zero--0.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by TheChaosTheory89 on 2007-10-13
> **taurus said:**
> You need to change the "default" setting in /boot/grub/menu.lst from Ubuntu to XP.  Remember,  each **title** counts as one and you start counting from zero--0.

```
gksudo gedit /boot/grub/menu.lst
```

Okay. Here is my MENU.LST, can you please and fix to make Windows highlight selection first, not ubuntu?

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
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=e9bbfdf5-ec7a-44a0-a013-a49e4aac3375 ro

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
 savedefault=true

## ## End Default Options ##

default 1

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive 1
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu 7.10
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9bbfdf5-ec7a-44a0-a013-a49e4aac3375 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

#title		Ubuntu 7.10 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9bbfdf5-ec7a-44a0-a013-a49e4aac3375 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd1,0)
#kernel		/boot/memtest86+.bin
#quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

---

### Post by taurus on 2007-10-13
Why don't you cut the text with the left button of your mouse and paste the code here with the middle button (or both right and left button at the same time if you don't have a middle button, or scroll wheel).

---

### Post by taurus on 2007-10-13
> **TheChaosTheory89 said:**
> Okay. Here is my MENU.LST, can you please and fix to make Windows highlight selection first, not ubuntu?

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
**[COLOR="Blue"]default		1[/COLOR]**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=e9bbfdf5-ec7a-44a0-a013-a49e4aac3375 ro

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
 savedefault=true

## ## End Default Options ##

default 1

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive 1
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu 7.10
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9bbfdf5-ec7a-44a0-a013-a49e4aac3375 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

#title		Ubuntu 7.10 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9bbfdf5-ec7a-44a0-a013-a49e4aac3375 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd1,0)
#kernel		/boot/memtest86+.bin
#quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and change the value from 1 to 0 in the blue highlight line above.  Save it and reboot.

---

### Post by TheChaosTheory89 on 2007-10-13
it didn't work when i reboot, the computer, i see GRUB menu

1. Windows XP Home Edition
2. Ubuntu 7.10 <-- was already highlighted, not on Windows?? WHY?

](*,)]

---

### Post by meierfra on 2007-10-13
> ## ## End Default Options ##

[COLOR="Red"]default 1[/COLOR]

title Microsoft Windows XP Home Edition.
root (hd0,0)
savedefault
makeactive 1
chainloader +1

You still have  a "default 1" statement in your "menu.lst".  Remove it

---

### Post by TheChaosTheory89 on 2007-10-13
it still does not work, when i boot up and the highlight would select on ubuntu, not windows? i have to manually, press up arrow keyboard to Windows

---

### Post by taurus on 2007-10-13
Can you post the latest version of your /boot/grub/menu.lst again?

---

### Post by TheChaosTheory89 on 2007-10-13
> **taurus said:**
> Can you post the latest version of your /boot/grub/menu.lst again?

Okay, this is a updated menu.lst, it still doesnt work!

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
default	1

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
# kopt=root=UUID=e9bbfdf5-ec7a-44a0-a013-a49e4aac3375 ro

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
 savedefault=true

## ## End Default Options ##

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive 1
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu 7.10
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9bbfdf5-ec7a-44a0-a013-a49e4aac3375 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

#title		Ubuntu 7.10 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9bbfdf5-ec7a-44a0-a013-a49e4aac3375 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd1,0)
#kernel		/boot/memtest86+.bin
#quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

---

### Post by meierfra on 2007-10-13
You did not change "default  1" to "default 0"

---

### Post by dinub1 on 2007-10-13
> **TheChaosTheory89 said:**
> it didn't work when i reboot, the computer, i see GRUB menu

1. Windows XP Home Edition
2. Ubuntu 7.10 <-- was already highlighted, not on Windows?? WHY?

](*,)]

You have twice "default=1" in your menu.lst. Delete to leave only one occurrence.
Why complicate yourself with it when you can select any OS you want at will at GRUB start?

---

### Post by meierfra on 2007-10-13
> You have twice "default=1" in your menu.lst. Delete to leave only one occurrence.

He did that already.

---

### Post by TheChaosTheory89 on 2007-10-13
> **meierfra said:**
> You did not change "default  1" to "default 0"

do i have to?

---

### Post by meierfra on 2007-10-13
> do i have to?
 
Yes,  'default 0' tells grub to highlight and  automatically boot  the first item in the grub menu. "default 1" boots the second  item  ( grub starts counting at 0)

---

### Post by TheChaosTheory89 on 2007-10-13
> **meierfra said:**
> Yes,  'default 0' tells grub to highlight and  automatically boot  the first item in the grub menu. "default 1" boots the second  item  ( grub starts counting at 0)

THANKS! IT WORKS! IT FINALLY SELECT ON WINDOWS! :popcorn:

---

### Post by dinub1 on 2007-10-13
U welcome. Glad you fixed it. On my menu.lst default is set at 0. I pick up whatever option I want. I also dual boot Ubuntu with Windows XP.

---

### Post by TheChaosTheory89 on 2007-10-13
> **dinub1 said:**
> U welcome. Glad you fixed it. On my menu.lst default is set at 0. I pick up whatever option I want. I also dual boot Ubuntu with Windows XP.

On two different hard drives? Mine does. Windows XP on 320 GB and Ubuntu 7.10 on 160 GB :KS

---

### Post by dinub1 on 2007-10-14
> **TheChaosTheory89 said:**
> On two different hard drives? Mine does. Windows XP on 320 GB and Ubuntu 7.10 on 160 GB :KS

Nope this is a laptop. Only one hard drive. But it has two partitions. 1st one is Win XP, 2nd one is Ubuntu 7.10. I have one desktop running 3 OS's one Windows 2000 Pro and two Linux distros on 2 separate HDD's.

---

### Post by motang on 2007-10-14
> **taurus said:**
> You need to change the "default" setting in /boot/grub/menu.lst from Ubuntu to XP.  Remember,  each **title** counts as one and you start counting from zero--0.

```
gksudo gedit /boot/grub/menu.lst
```
Wow thanks I was able to rem out the extra entries for Ubuntu, now the list isn't so big. :-D

---

