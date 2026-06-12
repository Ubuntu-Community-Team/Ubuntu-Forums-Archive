---
title: "installing questions"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by mikeftl on 2008-07-20
i have a few questions about instaling ubuntu.
i have windows vista and i want to dual boot onto the same harddrive as i have windows vista or put it onto my backup harddrive(has a few files in it).

If I install it will it make booting up windows any different? 
because i dont want to have to select which os everytime i start my computer. I would like to have it so if i want to use ubuntu, I can select it when i want, otherwise windows starts up as it did before.
Can I do that?
Also, I need some help installing.
Any easy to read (step by step) guides/tutorials out there? because i found alot of hard to read guides.

Thanks

---

### Post by Pumalite on 2008-07-20
First of all allocate space for Ubuntu with the Vista partitioner. Backup everything, but don't worry; this is costumary. If you follow this guide, you'll be fine:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Sef on 2008-07-20
> If I install it will it make booting up windows any different?
because i dont want to have to select which os everytime i start my computer. I would like to have it so if i want to use ubuntu, I can select it when i want, otherwise windows starts up as it did before.
Can I do that?

You will need to [change GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") to boot into Windows as the default.

> Any easy to read (step by step) guides/tutorials out there? because i found alot of hard to read guides.

Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by mikeftl on 2008-07-21
I need more help with the 

'Quote:
If I install it will it make booting up windows any different?
because i dont want to have to select which os everytime i start my computer. I would like to have it so if i want to use ubuntu, I can select it when i want, otherwise windows starts up as it did before.
Can I do that?
You will need to change GRUB to boot into Windows as the default.'

PArt

---

### Post by xen-uno on 2008-07-21
Open Terminal and type:
*sudo gedit /boot/grub/menu.lst*

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

[color=red]# Line below for custom splash (by SAJ) ... prevents highlighter from working for some reason ... disabled
# splashimage=(hd1,2)/boot/grub/xengrubsplash.xpm.gz[/color]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[color=red]timeout		15[/color]

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

[color=red]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows XP Professional x64 Edition
root		(hd0,0)
savedefault
makeactive
# Map functions below not neccessary when Windows is on 1st disk
# map		(hd0) (hd2)
# map		(hd2) (hd0)
chainloader	+1

# This is a divider, added to separate the menu items above from the Debian
# ones.
title		- v - - v - - v - Linux - v - - v - - v -
root[/color]

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
# kopt=root=UUID=6475b7eb-bc66-4b93-b603-61a598e622e3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

[color=red]title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,2)
# kernel	/boot/vmlinuz-2.6.24-19-generic root=UUID=6475b7eb-bc66-4b93-b603-61a598e622e3 ro quiet splash
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6475b7eb-bc66-4b93-b603-61a598e622e3
initrd		/boot/initrd.img-2.6.24-19-generic
# quiet[/color]

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6475b7eb-bc66-4b93-b603-61a598e622e3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

My modded (see red text) menu.lst contains the same number of code lines as original (except for the custom grub splash, which didn't work), but order has been changed as well as syntax and of course, the hd(x,x). I also want to see what is happening on bootup, which is why *quiet* is commented out in places. Be careful on editing yours for obvious reasons.

---

### Post by mikeftl on 2008-07-21
Does anyone have aim msn or yim i think that would be easier for me.

Do i have to type that on linux or can i do that on windows?

---

### Post by xen-uno on 2008-07-21
It's just a text file, so yes, you could do it in Windows with NotePad providing you install Ext2/3 read-write drivers. Make sure you understand completely the (hd x,x) labeling.

---

### Post by mikeftl on 2008-07-21
is there a guide that can help me step by step on how to do that??

---

### Post by xen-uno on 2008-07-21
I became enlightened after reading ...

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

and after jacking around with SuperGrub ... plus alot of trial & error

---

### Post by kajillin on 2008-07-21
[http://www.fs-driver.org/](http://www.fs-driver.org/)
for accessing linux partitions in windows

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
a how-to for tweaking dual booting

good luck,

---

