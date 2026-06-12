---
title: "Edgy to Fiesty. Monitor goes standby on normal boot, works fine in recovery mode."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by div- on 2007-04-20
Just upgraded from Edgy to Fiesty yesterday, and a strange problem surfaced. When I try to boot ubuntu, my monitor will go into standby mode (this is even before showing the splash-screen). Now I used to have this problem with Edgy, but I managed to solve it back then by editing my xorg.conf and deleting resolutions not supported by my monitor.

Not so much with Fiesty. The strange thing is, when I choose to boot in recovery mode, everything works fine. I'm currently at work so I can't test anything right now, but a colleague advised me to add acpi=off and noapic options to the bootloader so that will probably be the next thing I'll try. If anybody has another idea on what might be wrong, any leads would be much appreciated.

Some more info:
After going into standby, the system appears to hang, ie: caps-lock doesn't toggle the keyboard led anymore, ctrl-alt-backspace nor ctrl-alt-f1 work and the computer's reset button does not work either (I have to hold down power).

Graphics card is an ati x800, but as I said, it worked fine in Edgy, and it works fine when I boot using recovery mode. I'm also using the 64-bit version, but don't think that has much to do with it.

---

### Post by q*_*p on 2007-04-20
it seems to be similiar to my problem.
[http://ubuntuforums.org/showthread.php?t=414472](http://ubuntuforums.org/showthread.php?t=414472)

I have an ATI X700 card:
03:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

---

### Post by div- on 2007-04-20
Ok, I managed to resolve my problem by commenting out the splash option from /boot/grub/menu.lst

Would be nice if someone would be able to give some additional info as to why this would solve my problem, but for now at least I can properly boot.

---

### Post by Dabisu on 2007-08-25
Hi, I'm new to linux and ubuntu and I'm having the exact same problem. I'm at the menu.lst and I need to uncomment the splash option, but I don't really know how to do that. Can anyone help me out with this?

---

### Post by Pumalite on 2007-08-25
To uncomment something you add a # sign in front of it. But the slash option might be different in your menu.lst. So, post it and we'll help you.

---

### Post by Dabisu on 2007-08-25
Wow, thanks for the fast response and help! I have another question, which is probably really stupid, but I can't make any changes to the menu.lst file because I don't have privileges to write. How do I change this?

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
# kopt=root=UUID=d79707c1-4dcf-48af-844f-317b96fe13c8 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d79707c1-4dcf-48af-844f-317b96fe13c8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d79707c1-4dcf-48af-844f-317b96fe13c8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Pumalite on 2007-08-25
Third line below ###End Default Options###, kernel..bla,bla,bla, remove 'quiet splash' Or 5th line, where it says 'quiet', place # in front. Try this last first.

---

### Post by Dabisu on 2007-08-25
I tried both of those and it still crashes whenever I try to boot it. If I boot into recovery mode then exit I can get into Ubuntu fine. I read somewhere else that it was the graphics driver for my ATI card, but I did 

sudo dpkg-reconfigure xserver-xorg

as someone suggested on another topic.

Any advice?

---

### Post by Pumalite on 2007-08-25
What happened with dpkg-reconfigure?

---

### Post by Dabisu on 2007-08-25
I just went through each step setting it up, I enabled 1280 x 1024 resolution. Before I did dpkg-reconfigure I could see the desktop and everything, just now I have a higher resolution other than that I can see no difference.

I'm actually lending the computer to my Mom and it seems like it might be difficult for her to go through each of the steps to get it to boot through recovery mode. I'm not sure what else to try, mostly because I'm new to linux.

---

### Post by Pumalite on 2007-08-25
You could google you monitor for specs and then  edit your xorg.conf.

---

