---
title: "Bootmgr is missing"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by cespinal on 2008-06-14
hi ya all... 

im having a problem here.. 

I tried a couple of minutes ago and i got this: Bootmgr is missing

I guess something is happening in my vista partition..I could try using a recovery disk but my labbie didnt come with one... is there any way to repair this from ubuntu??? I (unfortunately) need to use vista at this moment.. .

thanks!!!!

---

### Post by meierfra. on 2008-06-14
You can get a recovery  CD from here:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by cespinal on 2008-06-15
thanks... Ill burn it tomorrow and see how it goes.. 

next time ill wipe off vista out! :lolflag:

---

### Post by cespinal on 2008-06-19
SO....got the recovery disc...booted it.. aaand: 

problem 1) it wont detect any of the partitions. I dont know which are  the drivers it asks me for. 

problem 2) after skipping this drivers thing, I try using the repair tools, which seem to run, but the same mgr error keeps popping up. 

any hints?

---

### Post by meierfra. on 2008-06-19
> un, but the same mgr error keeps popping up 

Are you dual booting?
Does this message appear when you select  Vista at the grub menu? 
Or are you trying to boot directly into Vista?

If you can boot into Ubuntu, post the output of

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```
(both 'l' are lowercase 'L')

---

### Post by cespinal on 2008-06-20
Indeed!, Im trying to boot windows vista from Grub. Ubuntu works perfectly tho. 

here's what you asked for: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa602a602

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26224   210644248+   7  HPFS/NTFS
/dev/sda2           26225       26542     2554335   82  Linux swap / Solaris
/dev/sda3           26543       28866    18667530    5  Extended
/dev/sda4           28867       30401    12329887+   7  HPFS/NTFS
/dev/sda5           26543       28866    18667498+  83  Linux


AND: 


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
# kopt=root=UUID=94d566ce-f91b-4273-80ca-cbb29b370078 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94d566ce-f91b-4273-80ca-cbb29b370078 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94d566ce-f91b-4273-80ca-cbb29b370078 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by meierfra. on 2008-06-20
The first Vista entry on the Grub menu should work. 

Where does the second Vista entry come from? Did you put it there?
Did  you delete any partitions, while installing Ubuntu?

Did you use Vista disk management to resize Vista? Or did you let Ubuntu do it?   In the latter case try

[URL="http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"]http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/
 [/URL]

You might also try:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

But since you are having problems with the recovery CD, I'm not sure that any of this will work for you.

---

### Post by Nikitas350 on 2008-06-20
When you installed vista did you have one disk plugged? I had a similar problem when i installed windows vista on a machine with 2 disks and vista putted the boot files in the second disk. As a result i wasn't able to boot using grub. I solved it by moving all the boot files from the second disk to the first (in vista's partition).

---

### Post by cespinal on 2008-06-20
> **meierfra. said:**
> The first Vista entry on the Grub menu should work. 

Where does the second Vista entry come from? Did you put it there?
Did  you delete any partitions, while installing Ubuntu?

Did you use Vista disk management to resize Vista? Or did you let Ubuntu do it?   In the latter case try


But since you are having problems with the recovery CD, I'm not sure that any of this will work for you.

1)I know, but Vista still does not work. 
2) I dont know where it came from, It has been like since I installed GRUB
3)Nopes, I have not deleted any partitions while installing Ubuntu
4) I used both, ubuntu a Vista so rezise partitions when learning how to do it. However, I didt that a long time ago and Vista was still working ok

Let me try your suggestion and then I'll report the outcome, 
Thank you for your help

---

### Post by cespinal on 2008-06-20
> **Nikitas350 said:**
> When you installed vista did you have one disk plugged? I had a similar problem when i installed windows vista on a machine with 2 disks and vista putted the boot files in the second disk. As a result i wasn't able to boot using grub. I solved it by moving all the boot files from the second disk to the first (in vista's partition).

Nopes, Vista came already installed in my HP Laptop... you know.. these things are "Vista certified"... 

Do you guys know where can I find a "Linux certified" sticker to place it over the Vista one? :lolflag:

---

### Post by caglar sekmen on 2010-03-30
I am not using vista and dual boot at all but I got the same message saying *bootmgr is missing* and it also says *press ctrl+alt+del to restart* which I did several times bot nothing happens.

---

### Post by PrototypeAlex on 2010-04-05
Your not alone on this one, I have just installed Ubuntu 9.04 and grub did not pick up windows 7 during the installation.

I've added a windows 7 boot command to /boot/grub/menu.lst, but now its coming up as "Bootmgr is missing".

I am trying to avoid using the windows 7 repair option because I have the feeling it will wipe over grub. Will keep searching to find an alternative solution.

---

