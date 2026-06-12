---
title: "WinXP and Ubuntu installed on different Hard Drives"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by roc320 on 2008-09-24
Hello everyone I'm trying to install WinXP on a 500 GB SATA 2 hard drive. I formated the drive to FAT32 using Ubuntu (specifically gparted).  

I have Ubuntu installed on a separate EIDE hard drive, my problem is that when I go to install WinXP on my SATA drive it keeps telling me that it wants to install info (MBR info) on my Ubuntu drive. 

I'm aware that WinXp does not like to be second in the pecking order, but is there a way to avoid having to reinstall everything all over again. Thanks

---

### Post by mike1821 on 2008-09-24
You should allow windows to install the MBR in your first drive and then simply re-install grub (the Linux boot loader).

Is a very simple process and it will not destroy anything else!

---

### Post by roc320 on 2008-09-24
Ok won't that mess up my Ubuntu hard drive and its info in some way? Thanks

---

### Post by caljohnsmith on 2008-09-24
You should go ahead and allow Windows to install its own MBR, because it unfortunately won't give you any choice anyway. :roll: Then ideally you should set your IDE Ubuntu drive to be first in the BIOS boot order, and make sure you have Grub installed to the MBR of the Ubuntu drive; then you should be able to boot Ubuntu fine and also Windows if you add it as an option to the Grub menu. The advantage of this is if anything happens to your Ubuntu drive, you should still be able to boot your Windows drive since it will have its own Windows MBR, not Grub. So if you can make your Ubuntu drive first to boot and would like to do this, let me know and I'll give specific instructions of how to go about it. :)

---

### Post by roc320 on 2008-09-26
Man sorry for the late reply. I have my EIDE drive with Ubuntu booting first (my PC always goes straight to Ubuntu after the boot order looks for a CD in the drive) so any instruction you can give me in order for WinXP to play nice with Ubuntu would be fantastic. Thanks in advance

---

### Post by madmak on 2008-09-26
edit your /boot/grub/menu.lst list youll find a few examples in the forum.
My menu.lst with a windows section looked like this
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
# kopt=root=UUID=1234ae4b-5d6e-42e5-9bbd-3babf14106ab ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1234ae4b-5d6e-42e5-9bbd-3babf14106ab ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1234ae4b-5d6e-42e5-9bbd-3babf14106ab ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1234ae4b-5d6e-42e5-9bbd-3babf14106ab ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1234ae4b-5d6e-42e5-9bbd-3babf14106ab ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title Other operating systems:
root

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
makeactive

### END DEBIAN AUTOMAGIC KERNELS LIST
```

add the windows part at the end of your grub list and edit the hd parts if needed to suit your setup. thats how i got it to run with 2 hard drives mate.
 then you just press esc when grubs loading and select windows.

---

### Post by caljohnsmith on 2008-09-26
Before I forget, one thing I forgot to mention is that it would be much better to format your Windows drive to NTFS rather than FAT32, because NTFS has better features suitable for Windows (including being able to handle files > 4GB if I remember correctly).

Is it too much trouble to temporarily disconnect your Ubuntu drive when you install Windows? Because if you can, that is about the best guarantee you can get that Windows won't touch your Ubuntu drive. :) But if you can't, if the Windows installer does say something about installing its MBR to your Ubuntu drive, don't worry about it, because you can always easily put Grub back in the MBR. Just make sure that Windows doesn't say anything about putting files on your Ubuntu drive (boot files, etc) as that could lead to lots of trouble.

Let me know how it goes or if you need more specifics/info. :)

---

### Post by roc320 on 2008-09-26
Wow thanks for the good advice guys. 

John that a great idea I can unplug the IDE connections and install windows that. Now what will happen when I boot the PC with all the drives connected? Thanks

---

### Post by caljohnsmith on 2008-09-26
If you can set your BIOS to boot your Ubuntu drive, that is the most ideal, because then all you have to do to boot Windows is add an entry for it in your Grub's menu, like madmak was talking about. Your Ubuntu should of course boot without any modifications, assuming it was booting OK before. Let us know how it goes or if you run into problems.

---

### Post by Pumalite on 2008-09-26
Check this too:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by roc320 on 2008-09-28
Ok guys I will give it a shot and let you know whats happening? Thanks

---

