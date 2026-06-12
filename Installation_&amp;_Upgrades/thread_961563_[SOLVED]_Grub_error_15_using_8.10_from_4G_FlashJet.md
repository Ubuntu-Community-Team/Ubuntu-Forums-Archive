---
title: "[SOLVED] Grub error 15 using 8.10 from 4G Flash/Jet Drive"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by speed32219 on 2008-10-28
Want to install 8.10 to 4 GB flash drive and boot from it for configuration and testing. (reason is early next week getting new Intel DG41FC MB and E5200 or E4700 Dual Core CPU. 

Went into Bios and disabled 1st HD (C with 8.04 installed). Changed Boot up sequence to DVD drive and Jet Drive (flash) as boot device 1 and 2 respectively.  Booted ISO image of 8.10 beta that I copied to a CD with Flash Drive installed in USB port.  Installed 8.10 Beta to Flash Drive, but when I boot from Flash I get error 15.  Now, when the system was installing to flash, it checked my current HW and found the 8.04 drive, so when it went to write Grub it asked me did I want to write to the 80GB drive C that I had disabled with 8.04 on it (Do not know how it found the drive since I disabled it in Bios, smart little sucker).  I said no and when asked where I want to put it I typed /dev/sdf (Flash drive) and it finished the installation without any errors.  I looked at the files on the Flash drive and the Grub foler is there.  When I do get the error 15 it gives meoptions to boot using 8.04 installed on the disabled drive.  Should I unplug all drives and install 8.10 Beta again to the flash drive or can I salvage the install by modifying a boot or ini file somewhere on the flash drive?

---

### Post by Pumalite on 2008-10-28
Post your menu.lst from your Flash drive

---

### Post by speed32219 on 2008-10-30
Sorry it has taken me some time to get back to you, but work is relentless.  Thank you for your help. I don't know why the smileys are there but they should be 8 in ().  Also, the only menu entry that does not give me an error 15 is the memtest one. 

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
# kopt=root=UUID=c8150635-9a5d-468b-ba60-3614ad2aa675 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd5,0)

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

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd5,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=c8150635-9a5d-468b-ba60-3614ad2aa675 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd5,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=c8150635-9a5d-468b-ba60-3614ad2aa675 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd5,0)
kernel		/boot/last-good-boot/vmlinuz BOOT_IMAGE=/install/vmlinuz file=/cdrom/preseed/ltsp.seed initrd=/install/initrd.gz quiet -- last-good-boot
initrd		/boot/last-good-boot/initrd.img
quiet

title		Ubuntu intrepid (development branch), memtest86+
root		(hd5,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=09c02783-2cd6-4e36-9c6d-ba5af72148b4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=09c02783-2cd6-4e36-9c6d-ba5af72148b4 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by panda726 on 2008-10-30
Grub error 15 refers to a file not found, on a partition that exists.  Try also editing the grub boot command (type "e" to edit the boot commands), and play with different root drives (your partition should be fine).  When you get a correct drive, you can edit your menu.lst to reflect this.  Different computers may have differing drive configs, so you may have to temporarily edit for other computers.

Tor

---

### Post by speed32219 on 2008-10-30
FYI, I have edited and added the menu.lst to my previous post.

Bump

---

### Post by speed32219 on 2008-11-01
Bump

---

### Post by Pumalite on 2008-11-01
Edit your menu.lst and change 'groot' and 'root' to (hd0,0)
Then make your BIOS boot USB first.

---

### Post by speed32219 on 2008-11-01
OMG, can it be so simple!

Never gave it a thought that when I made the USB Flash drive the 1st bootable device that it would look for hd0,0 instead of the hd5,0 that I made from CD using a working 8.04 with all my other drives installed.  DUH!

---

### Post by speed32219 on 2008-11-02
Everything is up and running.  Thank you Pumalite. 

By the way, my turtle beach sound card with optical spidf and wireless Trendnet 424UB were recognized right out the box.  That was not the case for Hardy.  Also installed envyng to clear up a display (EVGA GEforce 6200) problem.  Now it is 100% and works well using this 4 GB flash stick.

---

