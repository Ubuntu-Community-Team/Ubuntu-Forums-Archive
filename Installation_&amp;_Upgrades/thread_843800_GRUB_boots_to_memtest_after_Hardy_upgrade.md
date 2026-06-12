---
title: "GRUB boots to memtest after Hardy upgrade"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by k1dicarus on 2008-06-28
Hi everyone. My wife uses gOS Space. Practically Ubuntu with Avant Window Navigator installed by default. Today I decided to upgrade her system from 7.10 to 8.04 within the update manager. After rebooting her laptop, the computer goes directly to memtest. I checked out the GRUB menu and memtest was the only thing in the list. I popped in a liveCD and checked GParted to see what was up and 8.04 actually is there, we just can't access it! Anyone have any suggestions? This same thing happened to one of my laptops when 8.04 had just come out. I found a different thread that had to do with Dapper, and it told me to edit menu.lst by changing the 'default num' field, but before I did, I realized it's already on 0. Any help would be greatly appreciated! We would hate to lose some of the data we forgot to back up :(  Thanks everyone!

---

### Post by dstew on 2008-06-28
From the Live CD, open a terminal and post the output of```
sudo fdisk -l
```Does your 8.04 file system have a /boot/grub directory? If so, and if it contains menu.lst, please post the entire contents of the file.

---

### Post by k1dicarus on 2008-06-28
This is the output from the fdisk command:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c35e4c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

And the menu.lst:

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
# kopt=root=UUID=e8ad3097-2604-4812-bd9c-e03791f07455 ro

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

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Again, thanks!

---

### Post by Arenlor on 2008-06-28
I don't know why update-grub screwed you up, but from your GRUB your entries should be like:
title		Ubuntu 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e8ad3097-2604-4812-bd9c-e03791f07455 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e8ad3097-2604-4812-bd9c-e03791f07455 ro single
initrd		/boot/initrd.img-2.6.24-19-generic
Of course change the vmlinuz and initrd names to whatever they are in the /boot/ section. That should get you back into your system, once you're in it you should try: sudo update-grub then check it to make sure it's correct.

---

### Post by k1dicarus on 2008-06-28
Thanks for your answer! I'm not sure I understand it, however. I checked in the /boot/ directory and the only other file in that directory other than the grub folder is the memtest .bin file.

---

### Post by dstew on 2008-06-29
If you have no kernel images in the /boot directory, then Ubuntu has been mis-installed. Since there are no other operating system on that disk, go ahead and delete the partitions and install again.

---

### Post by upchucky on 2008-06-29
I wish the install/error messages did not scroll by so fast, it looks like it may have failed on a memory fault then installed the memtest for you.

watch the screen on the new attempt and hopefully it shows the errors if any, 
with any luck the install just failed (corrupt disk maybe)? and this time it will work.

---

### Post by @ndreX! on 2008-11-21
Actually i have the same issue... i look in the boot folder and there's only a memtest bin file.

There's any other option than re-install the operating system?

Thanks in advance.

---

