---
title: "edgy upgrade failure with duel boot"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by toddr on 2007-01-27
Maybe somebody can point me in the right direction. I waited to upgrade from dapper to edgy thinking I would avoid the problems, but I guessed wrong. I did the script upgrade recommended by Ubuntu. I have a duel boot system with XP (I wish I could dump XP but I need to keep it for now). I use the windows boot manager with grub on the ubuntu partition. I went through the upgrade script and it seemed to work fine until I rebooted. When I did so I selected the ubuntu partition then all I got was the word grub with a blinking curser next to it. At this point, I could do nothing. All that worked was to ctrl-alt-del and reboot. I can't access the ubuntu partition at all. Please help:confused:

---

### Post by geek_Man on 2007-01-27
Can you post your menu.lst file please?

---

### Post by toddr on 2007-01-28
forgive me for my ignorance, but what is the menu.1st file and where do I find it? When I get the word grub and a blinking cursur next to it, I can't type anything. All I can do is the ctrl-alt-del command to reboot.

---

### Post by geek_Man on 2007-01-28
Sorry, that would be my ignorance, not yours. You have the Live CD, right? If you do, boot up with that and go into the terminal and type "sudo gedit /media/name_of_hard_drive/boot/grub/menu.lst". The name_of_hard_drive is supposed to be the name of the drive with Ubuntu on it. All your drives should show up on the desktop. So anyway, just copy and paste all this stuff in the file into your post and I'll have a look.

You said that you were using the Windows boot manager with GRUB on the Ubuntu partition. What exactly do you mean?

---

### Post by toddr on 2007-01-30
Sorry for the delay. I use the windows boot loader on the mbr and grub on the second partition. Before the upgrade from dapper to edgy, this setup worked great. I'll have to download the live cd. I will post the results afterwards.

---

### Post by geek_Man on 2007-01-30
Okey dokey.

---

### Post by toddr on 2007-01-30
Well, my drives did not show up on the desktop. I don't know if this matters or not. Anyway, I did the command as you said and inserted /sda2 as my Ubuntu partition. The editor was blank. I then tried /dev/sda2 and I had the same results. I fired up the gnome partition editor to see if my partition showed up and it did. :confused:

---

### Post by louieb on 2007-01-30
The easy way to see your Linux files get [_[COLOR=Blue]Ext2IFS for Windows[/COLOR]_]("http://www.fs-driver.org/") Reads Writes EXT2/3 filesystems from Windows. This will let view your Linux files from windows.
or from the live CD go to Applications>Accessories>Terminal and Mount your Linux partition.
 
```
sudo mkdir   /mnt/ahdp
sudo mount -t ext3 /dev/sda2   /mnt/ahdp

```Now you can use gedit and open /mnt/ahdp/boot/grub/menu.lst.

---

### Post by toddr on 2007-01-30
okay that worked. here is the menu.1st file:
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
# kopt=root=UUID=75c8f7b6-3351-4802-b728-5bbc1ec9488a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=75c8f7b6-3351-4802-b728-5bbc1ec9488a ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=75c8f7b6-3351-4802-b728-5bbc1ec9488a ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=75c8f7b6-3351-4802-b728-5bbc1ec9488a ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=75c8f7b6-3351-4802-b728-5bbc1ec9488a ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=75c8f7b6-3351-4802-b728-5bbc1ec9488a ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=75c8f7b6-3351-4802-b728-5bbc1ec9488a ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by louieb on 2007-01-30
I know nothing about using the Windows boot loader. But from what I have read didn't you have to copy the Linux partitions boot sector  to someplace in windows? It may be you will have to go through the same stuff you did before to set up the windows boot loader to boot Linux.

Since I guess you don't know if the Edgy upgrade was successful, why don't you try [Super Grub Disk]("http://supergrub.forjamari.linex.org/")  a bootable cdrom, usb or floppy specially designed for the restore of boot. It can also boot a Linux install without modifying anything on the hard drive.

At least you should know if the upgrade was successful. Then if you don't want to mess with the windows boot loader you should check the Reinstall Grub and Dual Boot links in my signature.

---

### Post by geek_Man on 2007-01-30
The drive name wouldn't be sda2 or /dev/sda2, it would be something like "usbdisk". An actual name. If you did some snooping around, you'd be able to find it out. Als, it's menu.lst almost like menu.list, like list of things.  I would recommend getting the Super GRUB Disk if all else fails. BUT, it shouldn't. Go to the terminal and type "sudo fdisk -l". That, too, is "l" like "Linux".

---

