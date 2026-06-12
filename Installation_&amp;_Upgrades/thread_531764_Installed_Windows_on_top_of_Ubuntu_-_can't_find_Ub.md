---
title: "Installed Windows on top of Ubuntu - can't find Ubuntu"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by jmusso on 2007-08-21
I decided the other day that I needed to add Windows back onto my laptop to use video chat. My hard drive was partitioned as such, a main ext3 partition for ubuntu, a 1.43 gb partion for swap, and a 1.43 "extended" partition. I wanted to set up a dual boot on my laptop, so I loaded up the g-parted live disc, shrunk my linux partition, formatted the new 10gb partition to ntfs, and proceeded to pop in the XP disc to install it over that. However, after installing XP, there is no option to load Ubuntu! When I start my laptop it just loads XP. Help me please, I want my computer back.

---

### Post by merlinus on 2007-08-21
You can try to reinstall grub, which was no doubt overwritten by your xp install.

Boot from the live cd, and enter these commands one at a time in a terminal window:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y).

-merlin

---

### Post by jmusso on 2007-08-21
Do I need to have internet access to do this...?

---

### Post by merlinus on 2007-08-21
No.  Boot from the live cd, open a terminal window, and enter the commands one at a time.

-merlin

---

### Post by bigboy_pdb on 2007-08-21
You might want to try looking at this thread:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by jmusso on 2007-08-22
Hey, I did what you said and it worked fine. Except now I can't see my Windows partition? and when i hit esc while grub is loading, it only offers me about 30 different forms of Ubuntu. How do I get to a menu where I can choose between windows and ubuntu...?

---

### Post by jmusso on 2007-08-22
anything...?

---

### Post by merlinus on 2007-08-22
Post results of:

```

sudo fdisk -l
cat boot/grub/menu.lst

```

-merlin

---

### Post by jmusso on 2007-08-22
Thanks a lot for helping. Here's the results:
```
joe@joe:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        8267    66404646   83  Linux
/dev/hda2            8268        9542    10241437+   7  HPFS/NTFS
/dev/hda3            9543        9729     1502077+   5  Extended
/dev/hda5            9543        9729     1502046   82  Linux swap / Solaris
joe@joe:~$ cat boot/grub/menu.lst
cat: boot/grub/menu.lst: No such file or directory
joe@joe:~$ 


```

---

### Post by merlinus on 2007-08-22
My mistake.  Should be:

```

cat /boot/grub/menu.lst

```

-merlin

---

### Post by jmusso on 2007-08-22
```
joe@joe:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=b0e67e76-51cc-4668-81d5-e05188ed6ea8 ro

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

title           Ubuntu, kernel 2.6.20-16-lowlatency
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=b0e67e76-51cc-4668-81d5-e05188ed6ea8 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=b0e67e76-51cc-4668-81d5-e05188ed6ea8 ro single
initrd          /boot/initrd.img-2.6.20-16-lowlatency

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b0e67e76-51cc-4668-81d5-e05188ed6ea8 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b0e67e76-51cc-4668-81d5-e05188ed6ea8 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-lowlatency
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-lowlatency root=UUID=b0e67e76-51cc-4668-81d5-e05188ed6ea8 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-lowlatency
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-lowlatency (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-lowlatency root=UUID=b0e67e76-51cc-4668-81d5-e05188ed6ea8 ro single
initrd          /boot/initrd.img-2.6.20-15-lowlatency

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b0e67e76-51cc-4668-81d5-e05188ed6ea8 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b0e67e76-51cc-4668-81d5-e05188ed6ea8 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
joe@joe:~$ 

```

---

### Post by bigboy_pdb on 2007-08-22
At the end of my "menu.lst" file I have:
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I'm guessing that GRUB assumes that Windows should be on the first hard drive on the first partition and maybe that's why it didn't add your Windows partition to the boot sequence.

I think adding the following to the end of your "menu.lst" file should help:
```

title		Other operating systems:
root

title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

**[EDIT]**
I just wanted to give a brief explanation of why I used (hd0,0) for mine and (hd0,1) for yours. My Windows partition is on the first hard drive on the first partition and since the first hard drive is hd0 and the first partition is partition 0, it is listed as (hd0,0). Your Windows partition is on the first hard drive on the second partition (hda2) and since the first hard drive is hd0 and the second partition is partition 1, it is listed as (hd0,1).
**[/EDIT]**

---

### Post by merlinus on 2007-08-22
First of all, there is no windows entry in /boot/grub/menu.lst, so that is why that option does not appear.

Second, it looks like you have installed both generic and low-latency kernels for ubuntu.  Is there a particular reason for this?

Try adding these lines to the very end of the file, after 

### END DEBIAN AUTOMAGIC KERNELS LIST

```

gksudo gedit /boot/grub/menu.lst

```

title        Microsoft Windows XP
rootnoverify        (hd0,1)
savedefault
makeactive
chainloader    +1

And reboot.

-merlin

---

### Post by jmusso on 2007-08-22
Why do you use rootnoverify and the poster above you uses just 'root'? Just curious. thanks for all your help again, i'm about to try this out. 

I have both kernels installed, I think, because I installed Ubuntu Studio over the regular Ubuntu distro. Most of the **** doesn't even work though, and I can't figure out why. i.e. Virtual Keyboard and a lot of other things make no sound... anyways, let me try this out. thanks!

---

### Post by merlinus on 2007-08-22
If rootnoverify does not work, then change it to root.

Windows likes to be on the first partition, and since in your case it is second, rootnoverify might help.

-merlin

---

### Post by Caffeine_Junky on 2007-08-22
As -Merlin says,  Windows likes to be first-in-line, so if you still can not get your grub menu back, the next option IMO is to use [Super-Grub]("http://supergrub.forjamari.linex.org/") to boot into your linux partition. ..or re-install both your OS's  ie: Win + Ubuntu

ash

---

