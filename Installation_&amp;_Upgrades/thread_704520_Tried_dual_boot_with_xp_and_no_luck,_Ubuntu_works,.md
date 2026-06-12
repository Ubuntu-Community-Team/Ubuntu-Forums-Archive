---
title: "Tried dual boot with xp and no luck, Ubuntu works, how to re-install xp?"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by lebnan60 on 2008-02-22
Got fed up with xp so tried to dual boot into ubuntu.  I may have missed some steps. Now my Ubuntu works perfect but i can't get into xp. 

 I tried super grub with no luck and i tried manually changing the grub menu to add xp, it now shows up but i can't get into it.  I am using two different hd, one has xp and one has linux. All my files for xp are accessible through linux, but still can't boot into it. 

I'm still a beginner so my question is, do you know of any other way to try booting into windows. If not do you know the best way to re-install xp. I have all my crucial info backed up, but if i can save the install that would be great.

Any suggestions or anything would be great. Thanks

---

### Post by forestpixie on 2008-02-22
can you post the output of these from terminal

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by sandysandy on 2008-02-22
> **lebnan60 said:**
> Got fed up with xp so tried to dual boot into ubuntu.  I may have missed some steps. Now my Ubuntu works perfect but i can't get into xp. 

 I tried super grub with no luck and i tried manually changing the grub menu to add xp, it now shows up but i can't get into it.  I am using two different hd, one has xp and one has linux. All my files for xp are accessible through linux, but still can't boot into it. 

I'm still a beginner so my question is, do you know of any other way to try booting into windows. If not do you know the best way to re-install xp. I have all my crucial info backed up, but if i can save the install that would be great.

Any suggestions or anything would be great. Thanks

re-installing XP may not be necessary.

have a look at this site

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by lebnan60 on 2008-02-22
sudo fdisk -l:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97099709

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14334   115137823+  83  Linux
/dev/sda2           14335       14946     4915890    5  Extended
/dev/sda5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc008a693

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24791   199133676    7  HPFS/NTFS



**cat /boot/grub/menu.lst:**

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         5

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=2b6e92f9-1076-4a35-894e-60b0c5dbf992 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2b6e92f9-1076-4a35-894e-60b0c5dbf992 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2b6e92f9-1076-4a35-894e-60b0c5dbf992 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

---

### Post by forestpixie on 2008-02-22
you need to add XP to your menu list. Is that all of your menulist? - do you not have the bit that says '### END DEBIAN AUTOMAGIC KERNELS LIST'

back it up first

sudo cp /boot/grub/menu.lst /boot/grub/menu.bak.2202

open it for editing

gksudo gedit /boot/grub/menu.lst 

and add the bits to the end, assuming you haven't got the debian automagic bit - if you do and just missed it from post don't put it twice

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title Windows XP/Vista
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

the map bit I got from [here]("http://ubuntuforums.org/showpost.php?p=4375100&postcount=5") - to do with booting windows when it's not the first drive, hope that helps

---

### Post by lebnan60 on 2008-02-23
My apology, the "### END DEBIAN AUTOMAGIC KERNELS LIST" section was there, just missed it when i copied. 

I added the code and rebooted and entered the grub menu. The operating system was there but when i selected it this is what showed up:

Starting up...


NTLDR is missing
Press Ctrl+Alt+Del to restart

---

### Post by lebnan60 on 2008-02-23
So i searched the problem on google, it mentioned using the win xp installation disk and repairing windows. Would that mess up anything with my linux? Any suggestions?

---

### Post by forestpixie on 2008-02-23
it might muck up grub - can't remember at the moment, you're going to have to do it anyway afaik

but you can reinstall grub without too much trouble with either supergrub - burnt as an iso and boot with it, or with the buntu cd

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by lebnan60 on 2008-02-23
Alright i'll give it a shot. I have supergrub on disk already, so i got that covered. Thanks a lot for your help. :)

---

### Post by lebnan60 on 2008-02-25
Good news...it worked. Windows was going really slow, but then again thats why i switched. Rebooted back into ubuntu, and the option for windows is still in the grub menu.

---

