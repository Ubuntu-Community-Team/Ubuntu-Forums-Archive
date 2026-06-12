---
title: "boot loader question"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by sunflowertech on 2008-10-08
so ive just installed win XP and Ubuntu 8.04.a newbie at this. i read instructions a friend gave me.

i'm not such of a fan of the boot loader. is there anyway i could change it?

i want something like what windows had. i prefer all the OS on one list instead of having to enter somewhere in order to go into Windows.

Plus I did some additional installion so ... there's like 4 Ubuntu listed..can i reduce that?

---

### Post by cha0sthe0ry on 2008-10-08
Yes you can lower the number of Ubuntu things on your boot list.  On Gnome menu go to System > Administration > Startup-Manager.  Click on the Advanced tab at the top of the new window that comes up, and remove check marks in boxes next to Create boot option for memtest and recovery mode.

---

### Post by sunflowertech on 2008-10-08
are you sure abt that? i went to admin but nothing like start up manager

---

### Post by Gauvenator on 2008-10-08
You can do 
```
sudo gedit /boot/grub/menu.lst
```
And comment out the entries you do not need/want.  You can also set the default entry, so it will automatically boot windows.  Post a copy of you menu.lst and we can give you an example.

---

### Post by sunflowertech on 2008-10-08
i have 
Ubuntu 8.04.1, kernel 2.624-19 generic
(recovery mode)
Ubuntu 8.04.1, kernel 2.624-16 generic
(recovery mode)
Memtest 86+
Other OS
WinXP

What should I do?

---

### Post by Gauvenator on 2008-10-08
> **sunflowertech said:**
> i have 
Ubuntu 8.04.1, kernel 2.624-19 generic
(recovery mode)
Ubuntu 8.04.1, kernel 2.624-16 generic
(recovery mode)
Memtest 86+
Other OS
WinXP

What should I do?

Can you copy and paste your /boot/grub/menu.lst here?

---

### Post by sunflowertech on 2008-10-09
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
# kopt=root=UUID=aa6448e7-6168-4867-a93a-1f4c2f20f976 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aa6448e7-6168-4867-a93a-1f4c2f20f976 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aa6448e7-6168-4867-a93a-1f4c2f20f976 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=aa6448e7-6168-4867-a93a-1f4c2f20f976 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=aa6448e7-6168-4867-a93a-1f4c2f20f976 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
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

### Post by SteveNorman on 2008-10-09
save your current /boot/grub/menu.lst first

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

then open /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```

add number signs to the front of these lines, so that

```
title Ubuntu 8.04.1, kernel 2.6.24-16-generic
```

becomes

```
# title Ubuntu 8.04.1, kernel 2.6.24-16-generic
```

do this for all lines in the box below

```
title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=aa6448e7-6168-4867-a93a-1f4c2f20f976 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=aa6448e7-6168-4867-a93a-1f4c2f20f976 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,7)
kernel /boot/memtest86+.bin
quiet
```

and save.

The number signs "comment out" anything that you dont want the computer to read. So this saves your option to change the file at a later date while only displaying what is not commented out. This is the case for most configuration files.

---

### Post by robert shearer on 2008-10-09
> **sunflowertech said:**
> are you sure abt that? i went to admin but nothing like start up manager

System=>Admin=>Synaptic Package Manager.
When it opens use the search function and type in something like "start-up manager" or "startup-manager"
When it finishes the search then check the options by highlighting them and reading the properties box.
When you find the one you want then right click it, Mark for installation and Apply.
Once it is installed then System=>Admin=>Start-up Manager.

---

