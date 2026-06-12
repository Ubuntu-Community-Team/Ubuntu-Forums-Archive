---
title: "Grub error 13?"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by alanmzifa on 2007-10-22
Hi, I've just overwritten 7.10 Ubuntu Studio with Ubuntu 7.10. 
I run a 2 HDD set up with grub booting into Windows as default from the IDE drive that Ubuntu sits on. 
Windows lives on the SATA HDD.


My menu.lst seems fine (it's been set up like this for 6.06/7.04 and I don't understand what might be wrong with it but I can't get Windows to boot.


## ## End Default Options ##

title		Microsoft Windows XP OEM Home Edition
rootnoverfiy	(hd1,0)
savedefault 
map  		(hd1) (hd0)
map		(hd0) (hd1)
makeactive
chainloader 	+1


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6dd848f6-0a7b-4240-ac6a-423bdfede5a3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6dd848f6-0a7b-4240-ac6a-423bdfede5a3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Any help would be appreciated.

thanks

---

### Post by Wobedraggled on 2007-10-22
13 : Invalid or unsupported executable format
This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).

Windows  entry should look like this.

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

---

### Post by alanmzifa on 2007-10-22
Before your reply I unplugged my IDE drive and plugged it in again, then rebooted. This time (and each time) it boots straight through to Windows without giving me the boot menu (which it should as I have amended hiddenmenu.

I then tried what you'd suggested but no change. Machine goes straight through to Windows boot unless i hit the ESC button whereupon it brings up the boot menu.

Is GRUB corrupt or am I still missing something simple?

And  if GRUB is corrupt how do I re-install it?

---

### Post by alanmzifa on 2007-10-22
Just a polite bump...

---

### Post by meierfra on 2007-10-22
Could you post your whole menu.lst?  I would guess that you need to change the following:

hiddenmenu 

to 

#hiddenmenu

and if your want  to boot into ubuntu by default:

default 0

to 

default 1

---

### Post by jdfreshwater on 2007-10-22
It may just be a bios issue.  For some reason I've had this problem with my bios changing the boot order of my hard drives.

---

### Post by alanmzifa on 2007-10-22
meierfra, whole menu.lst below.

jdfreshwater, bios is set to boot IDE (Ubuntu and GRUB) first, SATA, (XP) second.


[B]Perhaps some people  could take a look at the menu.lst text below....
[/B]


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
timeout		7

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=6dd848f6-0a7b-4240-ac6a-423bdfede5a3 ro

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

title		Microsoft Windows XP OEM Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader 	+1


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6dd848f6-0a7b-4240-ac6a-423bdfede5a3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6dd848f6-0a7b-4240-ac6a-423bdfede5a3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by meierfra on 2007-10-22
Veyy strange: menu.lst looks fine. Just a very wild guess: Any chance you have a second menu.lst on your system? Could you  post the output of

```
sudo fdisk -l
```


To reinstall grub:

sudo grub

and at the grub prompt:

root (hd0,0)

setup (hd0)

quit

---

### Post by alanmzifa on 2007-10-23
sudo fdisk -l results...
[B]
Can someone please translate them....[/B]

monty@monty-desktop:~$ sudo fdisk -l
[sudo] password for monty:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65a5c086

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00bd00bd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7165    57552831   83  Linux
/dev/hdb2            7166        7476     2498107+   5  Extended
/dev/hdb5            7166        7476     2498076   82  Linux swap / Solaris
monty@monty-desktop:~$

---

### Post by alanmzifa on 2007-10-24
Just a polite bump...

---

### Post by meierfra on 2007-10-24
I kept staring at your fdisk and menu.lst, but can't figure out what is going on. Your  menu.lst and  fdisk look fine, except that I would have expected your ide drive to be listed first in fdisk since you seem to be booting from ide drive.   Just to cover all  the bases, could  you post  the output of 

cat /boot/grub/device.map

Did you try reinstalling grub? You might also  check all  your cables one more time.

But I don't have much experience with ide/sata combinations, so hopefully somebody with more knowledge jumps in.

---

### Post by alanmzifa on 2007-10-25
I didn't replace GRUB. I wanted to wait until someone had checked it over first.

Here is the output for 

monty@monty-desktop:~$ **cat /boot/grub/device.map**
**(hd0)   /dev/hdb**
monty@monty-desktop:~$


Do the menu.lst and that both look like they should?


thanks

---

### Post by alanmzifa on 2007-10-26
just a polite bump.

thanks

---

### Post by meierfra on 2007-10-26
Here are a few links   you might want to  look at:
[URL="http://ubuntuforums.org/showthread.php?t=351974"]
http://ubuntuforums.org/showthread.php?t=351974[/URL]

[http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")
[URL="http://users.bigpond.net.au/hermanzone/p15.htm#device.map"]
http://users.bigpond.net.au/hermanzone/p15.htm#device.map[/URL]


Based on those links  I suggest the following:

1)  Open  device.map via "sudo gedit /boot/grub/device.map" and add the line

(hd1) /dev/sda


2) Reinstall grub via:

sudo grub-install /dev/hdb

---

