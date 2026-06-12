---
title: "[SOLVED] Strange upgrade"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Don DeGregori on 2008-06-09
Hello,

Did upgrade from 7.10 a month or so ago (including Kubuntu session). All seemed to go well, but 2 peculiar bugs are still in place. They don't seem to hinder operation, but maybe someone can help me restore the system to "normal".

Here they are: During boot, up to login, all is verbose. I see every step in the process. And, (not so important I suppose), I don't hear the 2nd welcome music after password. I just hear the first drums at login.

I suppose most will say, "SO WHAT !". Others will say, so a fresh install. Don't think I want to do the later. Any ideas?

Don

---

### Post by Rallg on 2008-06-09
My no-problems 8.04 (both i386 and amd64) are more verbose than I would like them to be. Grub calls for "quiet" but apparently that's not enough. This applies both on boot and shutdown.

If no other problems, chill.

---

### Post by Rocket2DMn on 2008-06-09
Can you please post the contents of your grub's menu.lst file
```
cat /boot/grub/menu.lst
```

For your sound problem, check System->Administration->Login Window and check the Accessibility tab to see which sounds are set.

---

### Post by Don DeGregori on 2008-06-10
Re: Strange upgrade
[QUOTE]Can you please post the contents of your grub's menu.lst file
Code:

cat /boot/grub/menu.lst

For your sound problem, check System->Administration->Login Window and check the Accessibility tab to see which sounds are set./QUOTE]
__________________

[COLOR="Red"]I was able to to check login successful and add startup.wav. Now I get 2nd default sound. 1st sound was always there. Thanks. 
Don  [/COLOR]

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
timeout		3

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
# kopt=root=UUID=642626eb-20fb-4e7e-9598-eb16a836d47f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=642626eb-20fb-4e7e-9598-eb16a836d47f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=642626eb-20fb-4e7e-9598-eb16a836d47f ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=642626eb-20fb-4e7e-9598-eb16a836d47f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=642626eb-20fb-4e7e-9598-eb16a836d47f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=642626eb-20fb-4e7e-9598-eb16a836d47f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=642626eb-20fb-4e7e-9598-eb16a836d47f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=642626eb-20fb-4e7e-9598-eb16a836d47f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=642626eb-20fb-4e7e-9598-eb16a836d47f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Rocket2DMn on 2008-06-10
I don't see any reason for it to be showing a completely verbose boot.  I noticed on my laptop that it shows a bunch of text before it gets to actually booting the OS - at that point it goes to the splash with the boot lines below it (I removed "quiet" from the boot line).  Though it's not a usability issue, you can search [launchpad]("https://bugs.launchpad.net/ubuntu") for bugs like this, or report your own if you can't find one that matches your symptoms.

---

### Post by Don DeGregori on 2008-06-11
Thanks Rocket
At least I did manage to get back 2nd startup sound, I'm getting used to the verbose boot, so I guess I shouldn't complain. Both isues are very minor, I'll leave the verbose alone.
Don

---

