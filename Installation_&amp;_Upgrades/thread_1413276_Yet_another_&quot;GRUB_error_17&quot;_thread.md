---
title: "Yet another &quot;GRUB error 17&quot; thread"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2010-02-22
When I try to boot my Ubuntu 9.10 partition, by selecting any of the four choices (representing 3 kernel upgrades since the original, I guess), I get the infamous "Error 17: cannot mount selected partition."  How do I fix it, so I can boot Ubuntu 9.10 again?

This started happening yesterday, after I installed Ubuntu 8.04.4 LTS.  As I expected, it overwrote the GRUB2 boot loader that Ubuntu 9.10 had installed.  What I did not expect was the "cannot mount selected partition" stuff when trying to start my 9.10 install.

What gives?  I can boot 8.04.4, but not 9.10.  I can also still boot Windows 7 and XP, which were already there.

My hardware arrangement is somewhat complex.  I'll post the menu.lst file that Ubuntu 8.04.4 made if it will help.  Here's the basic setup:

One 1 TB SATA HDD:
-NTFS system partition (primary) for Windows XP
-NTFS partition (primary): only data, no system files

One 1 TB SATA HDD:
-NTFS system partition containing Windows 7
-NTFS partition (primary): only data, no system files
-ext3 partition (logical): Ubuntu 8.04.4 LTS filesystem root /
-Linux swap partition (logical)
-ext3 partition (logical): Ubuntu 8.04.4 LTS /home

One 160 GB SATA HDD:
-ext3 partition (primary): Ubuntu 9.10 filesystem root /
-Linux swap partition (logical)
-ext3 partition (logical): Ubuntu 9.10 /home
-ext3 partition (primary): general data storage, no system files

One 320 GB SATA HDD:
-NTFS partition (primary): only data, no system files

One 1 TB SATA HDD connected via eSATA:
-NTFS partition (primary): only data, no system files

Boot order in BIOS is set so that the first 1 TB HDD is the boot drive, and that's where GRUB is actually on the MBR.

It's probably something really stupid, like GRUB trying to mount the wrong partition when I choose one of the "Ubuntu 9.10" partitions in the GRUB menu.  But I don't know how to fix it.

I browsed the menu.lst file in my Ubuntu 8.04.4 install, though, and everything looks correct.  So I'm not sure where to start. :confused:

---

### Post by Objekt on 2010-02-22
FWIW here's menu.lst from the Ubuntu 8.04.4 LTS install:
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
# kopt=root=UUID=18d67d39-a557-4f8c-a277-8af6c7d881c4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=18d67d39-a557-4f8c-a277-8af6c7d881c4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=18d67d39-a557-4f8c-a277-8af6c7d881c4 ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=18d67d39-a557-4f8c-a277-8af6c7d881c4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=18d67d39-a557-4f8c-a277-8af6c7d881c4 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd1,4)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.10 (9.10) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 
initrd		/boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.10 (9.10) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.31-16-generic root=/dev/sdc1 
initrd		/boot/initrd.img-2.6.31-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.10 (9.10) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.31-17-generic root=/dev/sdc1 
initrd		/boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.10 (9.10) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.31-19-generic root=/dev/sdc1 
initrd		/boot/initrd.img-2.6.31-19-generic
savedefault
boot


```

---

### Post by Objekt on 2010-02-22
S-M-R-T!  I am so smart! :D

I fixed it by changing the "(hd2,0)" bit in my menu.lst file to "(hd4,0)."  Just like I suspected, the problem was one of hard drive enumeration.  I'm posting from my good old Ubuntu 9.10 install now.

Is there a way to refer to partitions by UUID when using an older GRUB?  I've been using GRUB2 so long I don't remember whether it was possible with legacy GRUB.  UUID's seem like a good way to avoid enumeration ambiguities, which bit me in the keister this last time around.

---

### Post by darkod on 2010-02-22
> **Objekt said:**
> S-M-R-T!  I am so smart! :D

I fixed it by changing the "(hd2,0)" bit in my menu.lst file to "(hd4,0)."  Just like I suspected, the problem was one of hard drive enumeration.  I'm posting from my good old Ubuntu 9.10 install now.

Is there a way to refer to partitions by UUID when using an older GRUB?  I've been using GRUB2 so long I don't remember whether it was possible with legacy GRUB.  UUID's seem like a good way to avoid enumeration ambiguities, which bit me in the keister this last time around.

Yes, I'm using grub4dos on usb stick to allow me to boot install files of different OSs. Just replace the root (hdX,Y) line with

uuid xxxxxxx

Should work fine.

---

### Post by b0b138 on 2010-02-22
Or...use grub 2 again [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Objekt on 2010-02-22
I could, but probably won't.  I'm not crazy about GRUB2.  While GRUB2 does have some advantages, it took an extra 20 or so seconds to boot for some reason.  Legacy GRUB is much quicker.

---

### Post by darkod on 2010-02-22
> **Objekt said:**
> I could, but probably won't.  I'm not crazy about GRUB2.  While GRUB2 does have some advantages, it took an extra 20 or so seconds to boot for some reason.  Legacy GRUB is much quicker.

Grub2 out of what ever reason adds some delay if grub2 is on one hdd and your ubuntu partition on another. Since you have multiple hdds this might have been the reason for the delay.
Sometimes you even think they are on same hdd but they're not. Depends if you checked or just assumed grub2 went to the ubuntu disk.

Of course, if grub1 works better for you, that's what you should use. I just said the above for someone else reading this, not trying to make you use grub2. :)

---

### Post by Objekt on 2010-03-02
Legacy GRUB's problem with hard drive enumeration bit me in the butt again this morning.  I'm not sure why the order changed, but I had to again fix a reference in my /boot/grub/menu.lst file to get Ubuntu 9.10 to boot.  That's a pain.  I think I'll switch back to GRUB2, 20-second delay and all.

---

### Post by oldfred on 2010-03-02
Since you have multiple hard drives, this is the minor grub2 bug that darko refered to:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc
Very long boot solved with experimental grub1.98 post8
[http://ubuntuforums.org/showthread.php?t=1367488](http://ubuntuforums.org/showthread.php?t=1367488)

For anyone with lots of drives, I suggest running this even for you own information. Whenever I am updating system I run the script before & after just to make sure I did what I really wanted to do.

You do not have to post unless you need some help understanding what the script produces:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

