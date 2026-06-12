---
title: "swap has been deleted - how to have one?"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by tralogik on 2008-01-07
Hi,

This morning when I booted my computer, I had Grub error 15.
Since I have Windows XP, Ubuntu 7.10 and Kubuntu 7.04 on the same machine I had to do a fixmbr to have at least XP to go onto the Internet.

Now, I want to use Ubuntu and Kubuntu again. So I put the live CD in and found that my swap file has 0 Mb used as you can see on the screenshot: [[img=http://img169.imageshack.us/img169/788/screenshotck4.th.png]](http://img169.imageshack.us/my.php?image=screenshotck4.png)
On that image, sda 1 is for XP, sda6+7 is Kubuntu, and sda 8+9 is Ubuntu (though I am not too sure about that, it could be the opposite),

How can I have my swap file back. I need to tell you that Ubuntu and Kubuntu shared the same swap file.

I am a new "Ubuntu drinker" and don't know that much. 

Thanks in advance!!

---

### Post by oldos2er on 2008-01-07
I see a 1 GB swap partition, with 0 MB used.

---

### Post by Bllasae on 2008-01-07
Can you run anything? Maybe the computer isn't reading it right, but if you had 0 swap space, then nothing would run, because swap space allows the computer to move files around when running them. Obviously, you're running an internet browser, whether it's on your computer or not, so it probably has swap space, but the computer doesn't recognize it. Try a fresh installation(reformat) and you can get it back.

---

### Post by tralogik on 2008-01-08
Hi Bllasae,

Well, according to the screenshot posted, I have 0 swap file. But you are right, I can use the internet.

If I try a fresh installation, will I lose all my data? Is it possible to reinstall only the swap file without losing anything? If so, what would be the process?

Many thanks!

---

### Post by zvacet on 2008-01-08
Download [Gparted]("http://gparted.sourceforge.net/) and with it take some space (2GB) from existing partition and make new partition and mark it as swap.

---

### Post by tralogik on 2008-01-09
Hi zvacet,

I have to boot Ubuntu with the live CD now. How can I download Gparted if I am working with the live CD, not with my "own files"?

Many thanks!

---

### Post by Gina on 2008-01-09
If you use the Live CD you already have it. See **System > Administration** menu - you should see partition editor.  There is also a Live CD available with just GParted on it but any Desktop Live CD should have it. Also, you can add any apps you want (within memory limits) from within a Live CD session using Synaptic Package Manager.

---

### Post by tralogik on 2008-01-09
Hi Gina,

My swapfile is there but there is a lock beside the name.

I found my boot menu and is as follows. Can anyone tell me if there is something wring with it. How can I boot again in triple boot?




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
timeout		30

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
# kopt=root=UUID=52aa2dc1-c807-487e-a9be-909fe4c0436b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Kubuntu, kernel 2.6.20-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=52aa2dc1-c807-487e-a9be-909fe4c0436b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Kubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=52aa2dc1-c807-487e-a9be-909fe4c0436b ro single
initrd		/boot/initrd.img-2.6.20-16-generic


title		memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		-----Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e50f28ae-b8f9-4221-a11d-ab437613880f ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e50f28ae-b8f9-4221-a11d-ab437613880f ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot

---

### Post by Gina on 2008-01-09
A lock beside the swap partition is normal.

Your menu.lst looks OK to me but you could try reloading grub.

Grub Error 15 means it can't find the kernel if I recall correctly.  I have had that in the past - I reinstalled since I was only testing anyway.

---

### Post by dabl on 2008-01-09
Grub errors are not caused by any condition of swap, AFAIK.  More likely, you have done something to change the ID of a partition listed in the /etc/fstab file, and now your /boot/grub/menu.lst file does not match your /etc/fstab file.  They have to match, with regard to the ID of the partition where the kernel is located.  For example, reinstalling an OS, including reformatting the partition, will change the UUID, and render the boot menu "obsolete", until you fix it.

If you can, boot a Live CD, open a console window and enter ```
blkid
``` and see how the output compares to the UUID's shown in your /boot/grub/menu.lst file for the bootable partitions.

---

### Post by tralogik on 2008-01-14
Hi guys,

Thanks for your help. I have decided to reformat and reinstall Ubuntu 7.10.

I really appreciate your help!

JS

---

