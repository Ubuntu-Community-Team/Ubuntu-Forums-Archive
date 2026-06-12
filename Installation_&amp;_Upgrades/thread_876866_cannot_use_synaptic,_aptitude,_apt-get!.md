---
title: "cannot use synaptic, aptitude, apt-get!"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by keplerspeed on 2008-08-01
Hi guys,

when I try to update or install anything, i get the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache

so i think great! easy fix! but if i run the dpkg --configure -a command as superuser, i get another error:

Cannot find /lib/modules/2.6.24.3.mykernel
update-initramfs: failed for /boot/initrd.img-2.6.24.3.mykernel
dpkg: subprocess post-installation script returned error exit status 1

so..... what do I do? Ive searched the net and have had no success, and I cant find this 'mykernel' module, either on my computer or anything about it. What is this mykernel thing, and how do i get it?? why has this happened? my system was running so smoothly....

Thanks.

EDIT: I have replaced my getopt file in /usr/bin, I did read that this file has caused problem... but its obviusly not the probem. I will continue searching about this mykernel issue

---

### Post by coffeecat on 2008-08-01
The label 'mykernel' is usually appended when someone compiles their own kernel. Are you sure you've never tried compiling your own kernel on that machine, or installed a kernel from a non-Ubuntu repository? 

Let's clarify a couple if things. Are you running Ubuntu and if so which version? Run 'uname -r' in a terminal and to see which kernel you are running.

This bit: 

> Cannot find /lib/modules/2.6.24.3.mykernel
update-initramfs: failed for /boot/initrd.img-2.6.24.3.mykernel
dpkg: subprocess post-installation script returned error exit status 1... looks as though it's trying to update the initrd image for the 2.6.24.3 mykernel (whatever that might be), but can't because it can't find the appropriate modules in /lib. 

Look in /boot to see what vmlinuz* (kernel) and initrd* files you have there. Also, what is in your /boot/grub/menu.lst? Can you boot with the 2.6.4-19-generic kernel (if you aren't already) which most of us are using?

---

### Post by keplerspeed on 2008-08-01
Thanks for the response coffeecat!

Ok I have tried to recompile my kernel (once, unsuccessfully) trying to solve my problem where my tv tuner driver (em28xx) will not install if i also have my webcam driver installed. ( [http://gkiagia.freehostia.com/2008/02/09/installing-avermedia-m115-drivers-on-ubuntudebian/](http://gkiagia.freehostia.com/2008/02/09/installing-avermedia-m115-drivers-on-ubuntudebian/) )

but thats a separate problem that im still resolving...

I have Ubuntu hardy 2.6.24-19-generic, I switched from win a few months ago and I (was) just getting confident with linux! I update regularly, and i even installed konqueror with aptitude only hours before I had this problem with all package managers. Im pretty sure I didnt do anything stupid!

in /boot/ i have

vmlinux-debug-2.6.24-19-generic
vmlinuz-2.6.24-16-generic
vmlinuz-2.6.24-18-generic
vmlinuz-2.6.24-19-generic

and

initrd.img-2.6.24-16-generic
initrd.img-2.6.24-18-generic
initrd.img-2.6.24-18-generic.bak
initrd.img-2.6.24-19-generic
initrd.img-2.6.24-19-generic.bak

my /boot/grub/menu.lst is

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
# kopt=root=UUID=d4e7d42f-b97f-4de5-8a13-9ccef555a4cd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d4e7d42f-b97f-4de5-8a13-9ccef555a4cd ro
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d4e7d42f-b97f-4de5-8a13-9ccef555a4cd ro single
initrd		/boot/initrd.img-2.6.24-19-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

ah ok well I did edit my menu.lst, as i wanted to clean it up when my computer first goes to the grup menu...(EDIT: by just deleting the options from the menu that i didnt want. i heard its asking for trouble removing previous kernels) i had all these kernel options that i didnt use. further, i edited the menu.lst so that i didnt have any splash screens of boot and shutdown, (EDIT: by removing the quiet splash and splash, [http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/](http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/) ) just so i could see the modules loading etc, splash screens are boring!! But im sure the package managers worked AFTER i edited the file.

I always boot the most update kernel: 2.6.24-19-generic

EDIT: I backed up my menu.lst before editing. i just replaced is so I have all kernel menus and splash screens. as I thought, this didnt help at all. Atleast we can assume this isnt the problem.

cheers

---

### Post by keplerspeed on 2008-09-02
I have done a reinstall of ubuntu. Atleast I dont have this problem anymore. A reinstall is not really a solution, but it worked!

---

