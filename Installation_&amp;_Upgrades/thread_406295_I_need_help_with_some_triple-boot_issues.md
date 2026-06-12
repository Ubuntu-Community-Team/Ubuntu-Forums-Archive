---
title: "I need help with some triple-boot issues"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by madscientist327 on 2007-04-10
I managed to triple-boot Windows XP Pro, Windows Vista Ultimate, and Ubuntu 7.04 beta. Now whenever I want to use Windows XP I have to navigate through two boot menus. Is there a way so that I can have only one boot menu that allows me to select any of the three operating systems? I also want to be able to choose an operating system that it will automatically boot into after a few seconds (Windows Xp). Please note that I am a Linux newbie and I just installed Vista and Ubuntu yesterday so I am unfamiliar with both. Any help would be appreciated thanks. :)

---

### Post by Swab on 2007-04-10
Perhaps if you post the contents of the file /boot/grub/menu.lst  then someone more wise than I will be able to assist :)

---

### Post by madscientist327 on 2007-04-10
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
# kopt=root=UUID=2aa628e8-2656-4765-a1ec-c4fb523eb884 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=2aa628e8-2656-4765-a1ec-c4fb523eb884 ro quiet splash
initrd		/boot/initrd.img-2.6.20-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=2aa628e8-2656-4765-a1ec-c4fb523eb884 ro single
initrd		/boot/initrd.img-2.6.20-12-generic

title		Ubuntu, memtest86+
root		(hd0,3)
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

---

### Post by Swab on 2007-04-10
Do you know on which partition XP is installed?  I'll take a guess.  

```
title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1
```

Try adding that you your /boot/grub/menu.lst and hopefully that gives you the option to boot to XP.  

 It looks like Vista has its own loader that lets you select between Vista and XP.  I wouldn't know how to alter that.

---

### Post by madscientist327 on 2007-04-10
Hmm... Didn't work.

It says "starting up..." and stays like that forever.

---

### Post by dreadlord_chris on 2007-04-11
Ya, the problem is that Windows has it's own bootloader - and all GRUB does is pass the ball to it when you choose the Windows option. So the answer to your first question, at least where GRUB/LiLo are concerned, is no - you're pretty much stuck with 2 boot menus. The thinking is to let foreign OS' handle their own booting - generally a good idea.

As to your 2nd question - yes, you can make any of the OS' listed on your GRUB menu the default, and set the *timeout* to be whatever you want.

The default you set here:
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

```
Change the **0** to the boot option you want to be default.
****NOTE****
[LIST=1]
[*]Counting starts at **0**
[*]Each line that starts with **title** in the boot menu list is counted as **1**
[/LIST]

The actual GRUB entries are at the end of the file (right after *## ## End Default Options ##*):
```

title Ubuntu, kernel 2.6.20-12-generic
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-12-generic root=UUID=2aa628e8-2656-4765-a1ec-c4fb523eb884 ro quiet splash
initrd /boot/initrd.img-2.6.20-12-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-12-generic root=UUID=2aa628e8-2656-4765-a1ec-c4fb523eb884 ro single
initrd /boot/initrd.img-2.6.20-12-generic

title Ubuntu, memtest86+
root (hd0,3)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```

So, keeping the 2 rules above in mind, if you wanted Windows as the default, you would set:
```

default 4

```
Now, as long as you **never** updated your kernel in Ubuntu, you'd be set. That's not likely to happen though. As soon as you updated your kernel a new option would be automatically added to your GRUB list, shifting everything and Windows would no longer be the 5th option :mad: . To fix this look for this section:
```

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

```
Just change that to true.

That will make GRUB default to the Windows bootloader after 10 seconds (unless you change the default timeout). As to the default setting for Windows. If I remember right Vista has its own bootloader, so you *probably* have to change it there. The only help I can give you there is that in XP you would right-click My Computer > Properties > Advanced tab > Startup & Recovery. In there you can change the default Windows to boot and adjust its timeout.

There might be 3rd party bootloaders out there that can get around the Windows one - I really don't know

Anyway, hope this help some....

p.s. to edit your GRUB menu:
```

sudo nano /boot/grub/menu.lst

```

[GRUB Manual]("http://www.gnu.org/software/grub/manual/html_node/index.html")

---

### Post by madscientist327 on 2007-04-11
Thanks for the help! :D

---

### Post by danketchpel on 2007-08-13
Thanks dreadlord_chris,

That helped!

I'm also triple booting, Ubuntu, Win 2k Pro, and Win 2K server.

It took a couple of trys to get the default count right but it worked.

It seemed like the older Grub menu (umm, RH 8 vintage)  was easier to edit.

---

