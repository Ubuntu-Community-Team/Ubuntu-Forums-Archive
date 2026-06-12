---
title: "Dual boot clarification"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by pippopappo on 2007-06-22
Hi everyone,

I'm a new user liking linux world, but i must work primarily on Windows.

I have this situation: PC with 2 HD, IDE primary master on which I installed Winodws 2000, IDe primary slave on which I installed Ubuntu 7.04. During Ubuntu installation I installed Grub on a floppy.
Following some documentation founded on line, I copied the floppy booting sector on Winodws disk (sudo dd if=/dev/fd0 of=/home/linux.bin, then I copied linux.bin on an USB disk from which I moved it on Windows disk C:\) and I configured it to dual boot by editing boot.ini file.

Now I have two scenarioes:
1) (typical) If I boot from primary master I can start both Windows (default) and Ubuntu.
2) If I boot from floppy I can start both Windows and Ubuntu (default).

If I set Bios to boot from primary slave nothing starts.
If the primary master will dead, I'd want to avoid to start linux ever from floppy, by booting from the primary slave (possibly without reinstalling everything). Briefly I'd want to transfer the floppy situation on the primary slave.

I tried by booting from floppy and the execute "sudo grub-install /dev/hdb" but in this situation if I choose Ubuntu from the boot list I get a black screen with the message "Error 17: Cannot mount selected partition", while if I choose Windows I get the same black screen with the message "Error 13: Invalid or unsupported executable format".

If this is useful I post the content of /boot/grub/menu.lst file and /boot/grub/device.map file:

****************** Begin menu.lst ******************

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0,
and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default
entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or
your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default
entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive
editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ce9ef31b-7163-41cb-ae75-1cb791045ddd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic
root=UUID=ce9ef31b-7163-41cb-ae75-1cb791045ddd ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic
root=UUID=ce9ef31b-7163-41cb-ae75-1cb791045ddd ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows 2000 Professional
root (hd0,0)
savedefault
chainloader +1

****************** End menu.lst ******************

****************** Begin device.map ******************

(fd0) /dev/fd0
(hd0) /dev/hda
(hd1) /dev/hdb

****************** End device.map ******************

Is there anyone that can help me?

Many thanks

Pippo

---

### Post by confused57 on 2007-06-22
If you ever need to remove your master drive...boot to your slave drive with Ubuntu, highlight your Ubuntu entry in your grub boot menu, press "e", then change root from (hd1,0) to (hd0,0), then press "b" to boot.(Note: You'll need to press "e" again before you can change the root entry).

This change is temporary, so it shouldn't hurt anything to test it with the master drive still connected to see if it works.

---

### Post by pippopappo on 2007-06-25
Many thanks for your suggestion: it works!!

Now I have two questions:

1) (just a clarification) "hd0" means ever the disk the PC booted from? Or it has a different meaning?
2) Is it possible to automate the process? I.E. is it possible that grub knows the disk the PC booted from and then it could use a menu item rather than another one? Or better, to have an single menu item that automatically run a command rather than another?

Many thanks for your support

Pippo

---

### Post by confused57 on 2007-06-25
> **pippopappo said:**
> Many thanks for your suggestion: it works!!

Now I have two questions:

1) (just a clarification) "hd0" means ever the disk the PC booted from? Or it has a different meaning?
2) Is it possible to automate the process? I.E. is it possible that grub knows the disk the PC booted from and then it could use a menu item rather than another one? Or better, to have an single menu item that automatically run a command rather than another?

Many thanks for your support

Pippo
1.) Yes, grub recognizes the first hard drive booted to as (hd0).
2.) I don't know of any automated process...I have an idea you can try, I've never tried it or even suggested it, but might be interesting to try:
Boot into Ubuntu, open a terminal, then add entries to the very bottom of your menu.lst to boot Ubuntu, if you boot to it first:
```
title Ubuntu, kernel 2.6.20-15-generic on hd0
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic
root=UUID=ce9ef31b-7163-41cb-ae75-1cb791045ddd ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode) on hd0
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic
root=UUID=ce9ef31b-7163-41cb-ae75-1cb791045ddd ro single
initrd /boot/initrd.img-2.6.20-15-generic
```

These entries would not be edited or deleted with a kernel update or if update-grub is run...won't hurt anything being there, but thought you might want to try.  These entries should boot your Ubuntu, if you boot first to your Ubuntu drive.

In fact, you could probably add an entry to boot Windows when you boot first to your Ubuntu drive:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

You might want to make a backup of your menu.lst, before editing it:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
```
then to edit menu.lst:
```
gksudo gedit menu.lst
```

Added:  The kernel line is usually just one line:
```
kernel /boot/vmlinuz-2.6.20-15-generic
root=UUID=ce9ef31b-7163-41cb-ae75-1cb791045ddd ro quiet splash
```
it probably just formatted that way when you posted, due to it's length?

---

### Post by confused57 on 2007-06-25
Deleted-double post

---

### Post by snobby500 on 2007-06-28
just a suggestion, if you read this, you may want to take a quick look at making a virtual machine, (if you dont know what this is, it alows you to run windows in linux or vice versa) if you do a lot of work with 3d, im not sure how well this will work however, just a suggestion.

2 programes i know of are:
virtualbox - ive used, very easy to set up
vmware - i dont know much about this, sorry :)

just putting it out there, cant hurt surely :)

---

