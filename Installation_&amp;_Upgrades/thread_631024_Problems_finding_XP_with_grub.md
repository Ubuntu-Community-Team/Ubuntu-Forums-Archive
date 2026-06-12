---
title: "Problems finding XP with grub"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by pettijok on 2007-12-04
So i just installed Ubuntu 7.10 on my laptop that has XP already on it and both installed on the same HDD. As of right now i have Ubuntu running fine and i can even reed and write to the files on my xp partition with ntsf-3g. Grub on the other hand cant find the xp partition to boot. I have been through the forums and worked through many different solutions with no success. But to my lack of experience in Linux in general i may have easily looked over something.

Here are some files that might help:

/boot/grub/menu.lst

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
# kopt=root=UUID=d2f7911c-776d-40ba-a357-91981689cc2b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d2f7911c-776d-40ba-a357-91981689cc2b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d2f7911c-776d-40ba-a357-91981689cc2b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

title Windows
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

========================================================


sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38fc268d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16065   156296384    78140160    f  W95 Ext'd (LBA)
/dev/sda5           16128   122881184    61432528+   7  HPFS/NTFS
/dev/sda6       122881248   136761344     6940048+  83  Linux
/dev/sda7       136761408   138753404      995998+  82  Linux swap / Solaris
/dev/sda8       138753468   156296384     8771458+  83  Linux

thanks for the help!

Kevin

---

### Post by mikewhatever on 2007-12-04
What do you mean by 'grub can't find it'. Do you see the option for Windows in the boot menu? Do you get any error messages?

---

### Post by pettijok on 2007-12-04
I mean grub cant find the xp partition. When i first installed Ubuntu i had no option to select  XP but after reading some posts i changed it to:

title Windows
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1

in the post above is the file i edited to change this. 

It now shows XP but i get Error 12: invalid device request

---

### Post by froy02 on 2007-12-04
From your fdisk -l check it shows your drive as sda which probably means it's SATA drive. IDE drives usually shows as hda (hd0) in linux.  I am not sure why ubuntu works with (hd0,5).

Anyway try this first. Increase timeout to 10 and comment out hidemenu in your menu.lst.  Or else you have to press ESC within 3 seconds to see the menu.  10 seconds is good time for timeout because if you're in a hurry just press enter to boot the default.

---

### Post by mikewhatever on 2007-12-04
Here's what I found on error 12 [http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_). Does it ring any bells? Have you had more then one Windows installations and deleted one of them at some point. According to start end figures of fdisk output, you seem to have some space missing before sda1, which I understand is an extended partition.

---

### Post by pettijok on 2007-12-04
> **froy02 said:**
> From your fdisk -l check it shows your drive as sda which probably means it's SATA drive. IDE drives usually shows as hda (hd0) in linux.  I am not sure why ubuntu works with (hd0,5).

Anyway try this first. Increase timeout to 10 and comment out hidemenu in your menu.lst.  Or else you have to press ESC within 3 seconds to see the menu.  10 seconds is good time for timeout because if you're in a hurry just press enter to boot the default.

Thanks froy02 the timeout and hidemenu were some nice tips, but i still seem to be stuck on this. I have been looking through link provided by mikewhatever but have been unsuccessful. Thanks for the help.

---

### Post by meierfra on 2007-12-04
> Have you had more then one Windows installations and deleted one of them at some point

How about answering this question? This is mostly likely the cause of your problems. The deleted Windows Partition contained  the information to boot your current Windows Partition.

---

### Post by pettijok on 2007-12-05
So in regards to your question i have only had one copy of xp installed. But i did have two partitions set up both ntsf. I used the Ubuntu install to reformat the second ntfs partition and installed Ubuntu. So XP might have had some of the boot info on the partition i reformatted for Ubuntu.

So in a attempt to fix this i took my XP cd and got to the recovery console and tried FIXMBR FIXBOOT and both said they had worked but once i rebooted i just had a black screen. So then i was left with nothing and reinstalled Ubuntu and am back where i started. Any thoughts?

---

### Post by Craigus on 2007-12-05
Any chance you can run gparted and post a screen shot of the partition structure ?

The reason I ask is that your partition arrangement looks odd and I wonder if the graphical representation might assist.

---

### Post by meierfra on 2007-12-05
As far as I can see you have two options:

1)   Deleted your windows Partition, create a primary partition in its place and reinstall Windows.

2)  Find some way to convert your extended  partition to a primary partition. For example if you have another hard disk with enough free space, you could create  an image of your Windows partition, proceed as in 1) and copy you image to the newly created primary partition.  You might also have a look at this [thread ]("http://ubuntuforums.org/showthread.php?t=552832") in particular [post 36]("http://ubuntuforums.org/showthread.php?t=552832#36")

---

### Post by meierfra on 2007-12-05
>  then i was left with nothing and reinstalled Ubuntu 

Just in case this happens again. You don't need to reinstall Ubuntu. Just Grub: See FixGrub or SuperGrub in my signature.

---

### Post by pettijok on 2007-12-06
Thanks for the tip :) I ended up saying screw it and formated xp and as of now i have nothing on it. I am now going to start from scratch and do a clean install with both. Defiantly starting to get a headache with all of this considering after i cleaned the hard drive of everything and tried to install i ran into more problems i didnt even have before. Last i looked this morning once the install was almost complete i got a error saying grub had a fatal error and couldn't install on drive.  

So for right now i guess im going to look for a good thread on a dual boot install along with check and see if their are any issues with my sony fs-660/w.

I am defiantly not liking sony right now as well with their little hidden recovery partition taking like 5 gigs and its ntfs as well.

---

### Post by pettijok on 2007-12-13
I would like to say thanks for all the help. I ended up reinstalling XP and ubuntu and was able to get them both booting right. I must say so far i am loving ubuntu and am using it as the main OS over XP. 

Thanks again.

---

