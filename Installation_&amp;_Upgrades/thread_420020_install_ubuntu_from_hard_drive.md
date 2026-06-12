---
title: "install ubuntu from hard drive"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Dave_34656 on 2007-04-23
Hi all

Ubuntu is so great that I would like to install on my Thinkpad 560x laptop so I can ubuntu on the move. However, it has no internal CD drive and won't boot from USB. A network install is also not possible.

What I'd like to do:

I can remove the hard drive and create a partition on it and put the ubuntu iso in there and put it back. I would like then to boot from that partition and install on the rest of the drive. This doesn't work though. It won't boot from a hard drive just with ubuntu cd iso on it.

So, my question is: what do I need to do to run the install off the same hard drive as I am installing to? I have googled and searched these forums but I can't find anything. If anyone can point me to a useful post or webpage that would be great.


Dave

---

### Post by silverbullet007 on 2007-04-23
I dont think what your wanting is possible.  Or at least Ive never heard of it.  Surely you could come in contact with an external cdrom drive to install from.  But if this laptop is so old that it didnt come with some sort of cdrom device then you might not want to run ubu on it.

---

### Post by silverbullet007 on 2007-04-23
But please let us know if you find anything on this.

---

### Post by Dave_34656 on 2007-04-23
Oh no. I hope it is possible. I actually have a external cd rom for it but it can't boot from usb or pcmcia even with help from a smart-boot-manager floppy. Also, I realise that the laptop is too old but I will probably switch the window manager to fluxbox to try and get round that.

Anyone have any more suggestions?

Dave

---

### Post by Xappe on 2007-04-23
you actually can install ubuntu from the **_alternative_ **iso-file (on hdd) with the use of the hd-media debian installer. But I think you'll need a boot floppy with grub, or something like that,  to get it going.
 
This is how I usually do my hd-media installs (with grub already on the disk):

1. [[COLOR="Red"]Download[/COLOR]]("http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/") and copy the hd-media files and the iso file to a partition on your drive that you will not use during install.

2. 
Make a grub entry (/boot/grub/menu.lst) that points to the right partition

something like

title Install Ubuntu
 root (hdx,y)
 kernel vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
 initrd initrd.gz

[COLOR="DarkOrange"](you should be able to do this from a grub boot disk too I guess, but i've never tried that myself)[/COLOR]

and run 
sudo update-grub

3. 
Boot

4. 
Install

---

### Post by louieb on 2007-04-23
Just for grins I swapped out the hard drive on two computers running Dapper.  Had a little hardware problem, had to reconfigure x. But got both to boot up. 
Even though the two computer have different brands of NIC cards,  didn't have a problem connecting to the network    I just wonder if you couldn't  put the drive on another computer and do a server install. Put it back and get a window manager using apt-get.

---

### Post by Dave_34656 on 2007-04-24
Thanks for your help. I don't really understand step 2 in Xappe's post. Where I am I supposed to do this? Is /boot/grub/menu.lst on the grub boot floppy? Do I do this using another computer? I know nothing about grub or  boot stuff.

Is this what I should be doing?: [http://www.linux-sxs.org/administration/grubflop.html](http://www.linux-sxs.org/administration/grubflop.html)

Also, am I supposed to personalise the suggested menu.lst script to suit my laptop, like the root (hdx,y)? Am I supposed to change x and y to something?

Sorry to pester.

Dave

---

### Post by Xappe on 2007-04-24
Since I haven't used a grub floppy myself, I don't know how it's configured, but I can tell you something about how it works on an installed system.

Grub has a drive/partition naming scheme that differs a bit from linux in a way it starts counting from zero. So if you want to point grub to the second partition on your first hdd it should be hd0,1 where the first number is the drive number and the second the partition number.

On your installed system the boot menu is configured from /boot/grub/menu.lst (a textfile) and on my freshly installed feisty fawn (tripple boot with windows and sidux) it looks like this:

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
# kopt=root=UUID=e7d37e4b-0b5f-4d1f-8f8b-be1099552346 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=e7d37e4b-0b5f-4d1f-8f8b-be1099552346 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=e7d37e4b-0b5f-4d1f-8f8b-be1099552346 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Debian GNU/Linux, kernel 2.6.20.7-slh-up-1 Default (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz root=UUID=f74d8d35-283b-4e29-a9b1-046f3388cbbc ro quiet vga=791 
initrd		/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Debian GNU/Linux, kernel 2.6.20.7-slh-up-1 (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20.7-slh-up-1 root=UUID=f74d8d35-283b-4e29-a9b1-046f3388cbbc ro quiet vga=791 
initrd		/boot/initrd.img-2.6.20.7-slh-up-1
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Debian GNU/Linux, kernel 2.6.20.6-slh-up-1 (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20.6-slh-up-1 root=UUID=f74d8d35-283b-4e29-a9b1-046f3388cbbc ro quiet vga=791 
initrd		/boot/initrd.img-2.6.20.6-slh-up-1
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Debian GNU/Linux, kernel memtest86+ (on /dev/hda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

Any additional boot entries should be added before

### BEGIN AUTOMAGIC KERNELS LIST 

or after

### END DEBIAN AUTOMAGIC KERNELS LIST

Hope cleared it up a little bit for you at least :)

---

