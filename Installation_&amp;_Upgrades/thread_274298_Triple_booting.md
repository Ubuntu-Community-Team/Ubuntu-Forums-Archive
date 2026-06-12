---
title: "Triple booting"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by cactaur on 2006-10-09
I've been using Ubuntu for a while, and decided a really enjoyed it. Now, I've decided to try other distributions of linux, so I decided to get Fedora Core 5. I originally had XP and Ubuntu, with grub as the boot loader. Now, I have Fedora, XP, and Ubuntu, all on seperate partitions, the problem is, grub doesn't detect Fedora. I tried, in the Fedora installation, to have Fedora set up the boot loader, but that still didn't work. If anyone can help me, that would be great. I tried asking on the red hat mailing list, I couldn't understand any of the answers given to me.

NOTE: My partitions are XP on hda1, Ubuntu on hda2, and Fedora on hda4.

---

### Post by Kateikyoushi on 2006-10-09
Can you give us your grub configuration ?
The menu.lst or grub.conf file depending on which distros you use.

---

### Post by cactaur on 2006-10-09
Yeah, here's my menu.lst.

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color green/light-gray 

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
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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


title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, kernel 2.6.17.7
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17.7 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17.7
savedefault
boot

title		Ubuntu, kernel 2.6.17.7 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17.7 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17.7
boot

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot


title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

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


```

I tried to alter this file many ways, but none worked.

---

### Post by Kateikyoushi on 2006-10-09
There is nothing about your other distro in it.
We need to know what kernel you use in fedora.
Can you mont that partition ? If possible show your other grub.conf or kernel name and path.

---

### Post by cactaur on 2006-10-09
Well, I never got INTO Fedora, but the web site says it uses the 2.6 kernel. I don't think I can mount it, but maybe I'm just not doing it right. I couldn't mount my /dev/hda4 drive if that's what you're talking about. And my Ubuntu kernel lies in /boot/initrd.img-2.6.15-27-386. As I said, not sure about Fedora, since I couldn't boot into it. If there's a method of getting into the Fedora partition from Ubuntu, I don't know of it.

---

### Post by cactaur on 2006-10-10
Anyone?

---

### Post by confused57 on 2006-10-11
Have you tried mounting your hda4 Fedora partition using this method:
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)
If you can get it mounted, you could possibly determine(open /boot/grub/menu.lst in Fedora) what entry to add to Dapper's grub to boot Fedora

Also, you might be able to reinstall Dapper's grub using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Maybe reinstalling grub will detect your Fedora install.

Looks like you dist-upgraded from Breezy to Dapper, from all your kernel entries in your menu.lst file.

---

