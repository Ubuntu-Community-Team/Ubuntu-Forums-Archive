---
title: "Too Many Booting options to Choose From"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by cornalsanders on 2008-07-24
I recently installed Ubuntu 8.04 and when I reboot the system - Dell 4100, with 2 hard drives a 40 gig and 60 gig - there are 6 booting options available. 3 of the booting options are duplicates of the other 3. I just want to be able to start my computer without having to choose any option, for I only have the one OS installed.

This is what I get at the boot up stage:

Ubuntu 8.04.1, Kernel 2.6.24-19 generic
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)
Ubuntu 8.04.1, Memtest86+
Other operating systems:
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (on /dev/sdb1)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)(on /dev/sdb1)
Ubuntu 8.04.1, Memtest86+ (on /dev/sdb1)


Thank you in advance for anyone able to help solve my issue.

---

### Post by Kevbert on 2008-07-24
Please post your /boot/grub/menu.lst file.  It may be that both menu options (the top three and the bottom three are exactly the same).  This file will confirm it.  To copy to here use the command ```
gedit /boot/grub/menu.lst
``` in terminal.  The file will then be shown in an editor.  To copy all select Ctrl+A and then Ctrl+C to copy.  Paste it in a post with Ctrl+V.

---

### Post by cornalsanders on 2008-07-25
Here is my /boot/grub/menu.lst:


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
# kopt=root=UUID=b994f16c-81c9-43e3-8550-9d35676a8d98 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b994f16c-81c9-43e3-8550-9d35676a8d98 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b994f16c-81c9-43e3-8550-9d35676a8d98 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3d346393-82e6-45b4-b239-942852944925 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3d346393-82e6-45b4-b239-942852944925 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by manishtech on 2008-07-25
Please tell while installation where did you install, in the 60GB hard disk or 40GB one?
You must have repeated the installation, that's why its coming twice!!

---

### Post by Kevbert on 2008-07-25
Which option do you normally select ?  Or do you select none and just allow the machine to boot.  Probably the easiest way would be to add # at the start of the lines for everything after these lines:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

```
then if everything works fine you can delete these lines later.  But as manishtech says it looks like you have installed Ubuntu twice (once on each hard disk as hd(0,0) is the first hard disk, first partition and hd(1,0) is the second hard disk, first partition.

---

### Post by cornalsanders on 2008-07-25
I did install the OS more than once, thinking reinstalling would some how solve my issue. Originally I had Windows XP, and there was a similar problem. So, I installed Linux again, but on the drive XP was on. 

I select the top choice, which is the 40 gig hard drive.

---

### Post by manishtech on 2008-07-25
> **cornalsanders said:**
> I did install the OS more than once, thinking reinstalling would some how solve my issue. Originally I had Windows XP, and there was a similar problem. So, I installed Linux again, but on the drive XP was on. 

I select the top choice, which is the 40 gig hard drive.
Before removing either of the Ubuntu installation you first need to find where exactly is GRUB installed. I would suggest you to find it out. When you get the list,press c to get to GRUB prompt.
Then type 
**find /boot/grub/stage1**
you can get some result like
hd0,X
and 
hd1,Y

now type
**root (hd0,X)**
and then 
**setup (hd0)**

Now you can format or delete the ubuntu on the secondary disk. Means the other one on 60GB...

---

### Post by Kevbert on 2008-07-26
> **cornalsanders said:**
> I did install the OS more than once, thinking reinstalling would some how solve my issue. Originally I had Windows XP, and there was a similar problem. So, I installed Linux again, but on the drive XP was on. 

I select the top choice, which is the 40 gig hard drive.

In the menu.lst the default boot item is the top listed item which is set by the line
```
default 0
```
(The next line would be 1 etc).
You could also reduce the time before the default item is booted by changing the line
```
timeout 10
```
to something less than 10 seconds.  It's exactly as it says on the tin (ie in the comments).

---

### Post by cornalsanders on 2008-07-26
> **manishtech said:**
> Before removing either of the Ubuntu installation you first need to find where exactly is GRUB installed. I would suggest you to find it out. When you get the list,press c to get to GRUB prompt.


How do I find out where the GRUB is installed, in order to get to the "pressing c to get to GRUB prompt."?

---

### Post by cornalsanders on 2008-07-28
I tried typing in 

find /boot/grub/stage1

but all I get is 

/boot/grub/stage1

---

### Post by zvacet on 2008-07-28
@ **cornalsanders**

Download [Gparted live cd]("http://gparted.sourceforge.net/") and with it delete Ubuntu from 40GB ( or from other drive ) and [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

