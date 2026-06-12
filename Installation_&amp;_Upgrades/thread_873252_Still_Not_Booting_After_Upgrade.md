---
title: "Still Not Booting After Upgrade"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by clbaines on 2008-07-28
Well I still cannot boot my Dell Inspiron E1505 after an upgrade using the upgrade manager. I went from 7.04 to 7.10. It will not boot. It goes to the Grub prompt. It does say that it is loading stage 1.5 before going to the
prompt.

I was given several things to try from an earlier post. Many were helpful and as a result I have much more information. This newest post is a restart.

From "fdisk -l" 

Device    Boot   Start      End       Id       System

/dev/sda1          1         7        de       Dell Utility
/dev/sdA2          8        269        b       w95 fat32
/dev/sda3  *      270       294       83       Linux
/dev/sda4         295       14593      f   	   w95 ext'd 
/dev/sda5         295       455       82       Linux Swap
/dev/sda6         456     14593       83       Linux		

Both /boot/grub/stage1  and /boot/grub/stage2 are in 
/boot/grub directory on /dev/sda6. At the Grub prompt
I did  find /boot/grub/stage1 and it retuns (hd0,5). 
When I boot into a live cd and look in /dev/sda6 or (fd0,5)
and look in /boot/grub both stage1 and stage2 are there.

device.map 
(fd0)  /dev/fd0	
(hd0)  /dev/sda

There is no menu.lst file on this computer. It does not 
exist. It is not in  /boot/grub and sudo find menu.lst retuns
a file not found.

I have tried the following procedure as suggested.
root hd(0,5)
kernel /boot/vmlinuz-2.6.22-15-generic
initrd /boot/initrd.img-2.6.22-15-generic
Both are on dev/sda6
At the grub prompt:  find /vmlinuz  returns   (fd0,1)


I should note that I never get a chance to use initrd as kernel /boot/.......
Returns the error message "kernel not found"  I tried it with the old kernel with
the same result. I was hoping this would work.

I am missing something here and I just can't get it going.

---

### Post by mssever on 2008-07-29
> **clbaines said:**
> There is no menu.lst file on this computer. It does not 
exist. It is not in  /boot/grub and sudo find menu.lst retuns
a file not found.
There's a good chance that's your problem. How can GRUB set up its menu without that file? Try re-creating /boot/grub/menu.lst. It's owned by root:root with permissions 0644. Here's mine for an example (though you'll probably have to modify it some):
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        1

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=cf40ebf3-808f-4ab6-b7d9-52bf598a33b2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=splash quiet

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cf40ebf3-808f-4ab6-b7d9-52bf598a33b2 ro splash quiet
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cf40ebf3-808f-4ab6-b7d9-52bf598a33b2 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        System Recovery OS (ThinkPad)
root        (hd0,1)
savedefault
makeactive
chainloader    +1

```
Perhaps the easiest thing would be to install it where it belongs (from a live CD or similar), edit the Windows stuff and the configuration section, then chroot to your install and run [FONT=Courier New]sudo update-grub[/FONT].

---

