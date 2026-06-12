---
title: "Kernel Upgrade to 2.6.24-21-generic"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by philgenius on 2008-10-21
I had upgraded the linux kernel to 2.6.24-21-generic, and as soon as that occurred, I got random freezes of the entire system! Alt+PrintScreen+R+S+E+I+U+B did not have any effect. The freezes also occurred twice when I watched a youtube video while simultaneously downloading a torrent using Transmission.

Is this related to the new kernel, or is it just me?

UPDATE: The problem appears to be stemming from Transmission, because every time I restart it up, the computer freezes in x amount of minutes. Any ideas?

---

### Post by godfree2 on 2008-10-21
[http://ubuntuforums.org/showthread.php?p=5979677](http://ubuntuforums.org/showthread.php?p=5979677)

---

### Post by steveneddy on 2008-10-21
It is wise at this point to avoid the -21 kernel.

Many users are having issues.

---

### Post by alexcckll on 2008-10-22
So... the best idea would be to do what I've done - and stick to only downloading critical Security updates for the time being?

Is Canonical going to supply a list of certified hardware that the the -23 or future kernels will behave on?  

I'm a Lotus Notes admin.  as far as this laptop I'm on at the mo, I'm more of a *user* of Ubuntu; I bought this Thinkpad R61i from Linux Emporium already preinstalled and preconfigured.

Ideally - it would be better for the platform testers to roll out a web page which, when major kernel updates come out, could list the hardware that is certified against the new update.

This way - if end-users are waiting for fixes.. ESPECIALLY if they bought the machine preinstalled, it's a lot easier to look for whether kernel 2.6.24-35 (for instance) isn't going to break an Acer Aspire 1, or a Lenovo Thinkpad <model>.... rather than looking for specific chipsets.

As more and more netbooks are released.. looking for chipsets is fine IF you've built a machine... but if all you did was buy a Linux-preloaded laptop...

THoughts?

---

### Post by philgenius on 2008-10-22
So how do I degrade to -19? Just uninstall the -21 packages thru Synaptic and "reinstall" -19 packages?

---

### Post by Pumalite on 2008-10-22
Post:
cat /boot/grub/menu.lst
Also tell me what do you have in your Grub folder

---

### Post by philgenius on 2008-10-22
```
philip@1951-44U:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=50062686-2a66-46bc-9490-6bdbc9befc47 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=50062686-2a66-46bc-9490-6bdbc9befc47 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=50062686-2a66-46bc-9490-6bdbc9befc47 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=50062686-2a66-46bc-9490-6bdbc9befc47 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=50062686-2a66-46bc-9490-6bdbc9befc47 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
philip@1951-44U:~$ 

```

And for the Grub folder...check attachment.

---

### Post by Pumalite on 2008-10-22
Just comment out (put a # in front) of these lines in your menu.lst:

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=50062686-2a66-46bc-9490-6bdbc9befc47 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=50062686-2a66-46bc-9490-6bdbc9befc47 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

Then boot with your 19 kernel

---

### Post by philgenius on 2008-10-22
Hahaha....even with downgrading the kernel the freeze still happens. I think this has something to do with running YouTube and Transmission at the same time. I dunno. Any ideas?

---

### Post by Pumalite on 2008-10-22
At which point the 'freeze' happens? Could you give more details?

---

### Post by philgenius on 2008-10-23
I started Transmission with a torrent that would download a couple gigabytes worth of video. I then started watching YouTube, and after approximately three minutes, the entire system froze. No response from mouse, keyboard shortcut mentioned above, nothing. I had to hold down the power button to restart.

This will happen even though the YouTube video isn't playing, but is on the current browser.

Anything else needed?

P.S. For now, I brought back the -21 kernel because several apps had their dependencies built on top of the -21 kernel. Other than this, there were no other problems.

---

### Post by alexcckll on 2008-10-25
Thinking how much hassle people have been having with -21, I just whacked this into Brainstorm.... 
[Proposing a Model-Office repository and test stage for Ubuntu...]("http://brainstorm.ubuntu.com/idea/14802/")

This being a place where *multi-package* apps can go for user-acceptance testing and wider testing before release to the end-users.

---

