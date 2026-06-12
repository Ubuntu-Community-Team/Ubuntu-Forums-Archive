---
title: "Upgrade to feisty: waiting for root file system - alert! /dev/sda1 doest not exist"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by eombah on 2007-04-20
Hi,

I pressed the Upgrade to 7.04 button from the Edgy Update Manager.
It asked me something about lvm and raid. I did not really understand what is was asking me, so I accepted the default, which was "All". Afterwards, I think it was asking me where to look for raid partitions under lvm. So I guess I answered "look on all lvm partitions".

It started downloading, I left to take a shower (just got back from a conference in the states :-) ), when I returned I saw all sorts of colored lines on the screen. Nothing worked anymore, i  had to cold boot it.

Now when it starts up, it says it's starting up RAIDs and that it's waiting for the root file system.
Then it says: ALERT! /dev/sda1 does not exist, dropping to a shell.
Then I get a non-reponsive busybox shell.

please help.

Bart.

---

### Post by Helmi on 2007-04-21
the same goes for me. It fails to assemble all arrays as it finds no devices listed in the conf. (there is no raid though)

---

### Post by eombah on 2007-04-21
i don't have raid setup either.

is there a quick soloution to this problem, to get my computer running again?

---

### Post by useResa on 2007-04-21
PREREQUISITE: In my /boot/grub/menu.lst I have both the generic and the 386 kernel

I ran into a similar situation and was able to complete the upgrade by doing the following:
After restarting my computer and pressing ESC quickly enough selected the 2.6.17-11-386 kernel (instead of the 2.6.17-11-generic one). This installation started.
Now in a terminal gave the command
```
sudo apt-get update && sudo apt-get dist-upgrade
```This resulted in a completed upgrade.

Now modified the menu.list with ```
gksudo gedit /boot/grub/menu.lst
```Put the 2.6.20-15-generic kernel on, followed by the recovery mode version for this kernel. This followed by the 2.6.20-15-386 kernel and the recovery mode version.
Removed all the others.
So now it looks like this> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro

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
# defoptions=quiet splash vga=791

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

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
boot

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.20-15-generic
boot

title        Ubuntu, kernel 2.6.20-15-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.20-15-386
savedefault
boot

title        Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.20-15-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LISTRebooted and had a running feisty version.

Still had some (minor) issues to resolve but at least I had the upgrade installed and could start improving from there on.

Hope this will help you to.

---

### Post by eombah on 2007-04-21
I got it running again. my boot menu listed two kernels:

2.6.17-11 generic
2.6.17-10 generic

selecting 2.6.17.10- generic allowed the system to boot gain, so I'm apt-get dist-upgrading now.

cheers Bart.

---

