---
title: "upgrade problems with edgy"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by siddharth_s on 2006-11-26
hi,
i downloaded an alternate installation cd from one of the mirrors. using it i updated my dapper install to edgy (using terminal commands and not software update manager).
when the pc rebooted the xserver was corrupt. then i reinstalled the package ubuntu-desktop from apt.
the xserver started working fine but there is not startup screen saying "UBUNTU" with the progress bar.
instead it shows terminal commands. please help.
siddharth shroff

---

### Post by bapoumba on 2006-11-26
Hi,
can you post the output of **cat /etc/boot/grub/menu.lst** ?
In the kernel line, you should add splash (after quiet)

---

### Post by siddharth_s on 2006-11-28
hi,
there is no such folder called boot in etc.
in the terminal it shows cat: /etc/boot/grub/menu.lst: No such file or directory
HELP

---

### Post by bulldog on 2006-11-28
Try```
cat /boot/grub/menu.lst
```
And please no panic,you can boot perfectly without the splash-screen I suppose.

---

### Post by bapoumba on 2006-11-28
Sorry ... Yes, /boot/grub/menu.lst :/

---

### Post by siddharth_s on 2006-11-29
hi,
this the file listing for menu.lst

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=304def12-19c7-4575-b395-ac38e1e22a0e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=304def12-19c7-4575-b395-ac38e1e22a0e ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=304def12-19c7-4575-b395-ac38e1e22a0e ro single
initrd          /boot/initrd.img-2.6.17-10-386
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-27-386 root=UUID=304def12-19c7-4575-b395-ac38e1e22a0e ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-27-386 root=UUID=304def12-19c7-4575-b395-ac38e1e22a0e ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-23-386 root=UUID=304def12-19c7-4575-b395-ac38e1e22a0e ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-23-386 root=UUID=304def12-19c7-4575-b395-ac38e1e22a0e ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

hope its of some help....

---

### Post by bapoumba on 2006-11-29
The file looks okay. Do you have usplash installed ?
The current edgy version is :
```
usplash:
  Installed: 0.4-33
 *** 0.4-33 0
        500 http://fr.archive.ubuntu.com edgy/main Packages

```
You may have to reinstall it.

---

### Post by siddharth_s on 2006-12-05
hi,
sorry i was ill so couldnt reply... hey the above code doesnt work help........

---

### Post by bapoumba on 2006-12-05
Just check in synaptic if usplash is installed, or in a terminal : **apt-cache policy usplash**.

---

