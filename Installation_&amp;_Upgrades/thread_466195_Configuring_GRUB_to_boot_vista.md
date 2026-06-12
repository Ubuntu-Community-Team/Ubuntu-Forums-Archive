---
title: "Configuring GRUB to boot vista"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Catdaemon on 2007-06-06
Hey guys, I just installed Ubuntu 7,1 and it's gone wonderfully, I have everything set up as I want it. My issue is that after installation my Vista installation is completely inaccessible (the files are fine, just the OS). I formatted my (previously) XP drive (/dev/hdb) which is 9 gigs and installed Ubuntu on it, leaving the Vista installation (on /dev/sda) alone. Was I wrong to expect the installer to autodetect it? Anyway, I've messed about with Grub for a bit and not had any luck, so what's the best way to do this?
I have done a few searches but haven't found a solution to this problem yet.

---

### Post by esavato on 2007-06-06
When I installed Ubuntu FF, I used the Vista disk resize / format utility to handle the drive resizing...  I have heard of some issues with the live cd breaking the Vista mbr, making Vista inaccesable.  I would suggest putting in your Vista DVD and doing a repair on it.  You can also play arround with the grub menu.lst /boot/grub/menu.lst and trying to manually input Vista into the loader...

---

### Post by Catdaemon on 2007-06-06
I did both of those. Unfortunately neither worked, thanks anyway. If indeed the vista installation is broken it's not that big a deal, all it means is that I can give more space to Ubuntu :D

---

### Post by confused57 on 2007-06-06
Might help if you can post your menu.lst, open a terminal:
```
gedit /boot/grub/menu.lst
```

---

### Post by Catdaemon on 2007-06-06
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
# kopt=root=UUID=bbc5215b-27a5-4958-b694-65461103bb7c ro

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

title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bbc5215b-27a5-4958-b694-65461103bb7c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bbc5215b-27a5-4958-b694-65461103bb7c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I tried a few things in the "windows vista" part, willing to try anything really.

---

### Post by confused57 on 2007-06-06
You could try map commands in your Window's entry:
title Windows Vista
root (hd1,0)
savedefault
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader +1

Believe you've done quite a bit of editing in your menu.lst, you might also want to post the output of:
```
gedit /boot/grub/device.map
```
and
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by detroit/zero on 2007-06-06
I had a similar mix-up after dual booting a laptop i recently purchased that came with (of course) Vista pre-installed. First, installing Ubuntu broke the Vista/Longhorn bootloader. Then re-installing Vista wiped Grub out of the picture and took the computer back over. I found these two links and between the two of them, I got everything working just fine.

```
http://www.linuxquestions.org/questions/showthread.php?t=542585
```
```
https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows
```

Good luck!

---

### Post by Catdaemon on 2007-06-07
> **confused57 said:**
> You could try map commands in your Window's entry:
title Windows Vista
root (hd1,0)
savedefault
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader +1

Believe you've done quite a bit of editing in your menu.lst, you might also want to post the output of:
```
gedit /boot/grub/device.map
```
and
```
sudo fdisk -l
```
the -l is a small "L"

<snip>
OK! Everything loads properly now.. except "NTLDR is missing", which I assume can be fixed using the vista CD.

---

### Post by Mark Phelps on 2007-06-07
The default Ubuntu installation puts GRUB into the MBR of the first hard drive.  Unfortunately, Vista does exactly the same thing -- without providing you an option to put it somewhere else.  When you do the Vista "repair", that will "fix" Vista by overwriting the MBR with the info needed by the Vista boot loader. If that's the same MBR that currently holds GRUB, then you'll lose the ability to boot GRUB, and will then have to reinstall GRUB -- this time, to a partition instead of to the MBR.

---

