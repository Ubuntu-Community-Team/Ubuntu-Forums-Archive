---
title: "Dual-Boot Recover Vista HELP"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by eagledrc on 2008-05-21
Hey,

I had a dual-boot between Vista (32-bit) and Hardy Heron (64-bit), it worked great.  But I wanted to switch to 32-bit Ubuntu, so I deleted the Hardy Heron partition from Vista.  I then discovered that I had deleted GRUB as well.  I installed Ubuntu on the portion of the drive that Vista was not using; I made a new partition from the Live CD.  There was still 312GB left that Vista was on, and I could view my Windows files from the live CD.  However, after I installed it, GRUB didn't show Vista, and I can no longer see the Windows files on Ubuntu.  A Vista Recovery Disc didn't help.  What can I do?  I have a 380GB HD, and I had 312GB dedicated to Vista, and 68GB to Ubuntu.  On Nautilus, it says that I have 60GB left of free space, meaning that I installed it on the right partition and the Windows stuff is not erased because then I would have 300GB of free space.  Please Help!!! I don't care so much about my Vista install itself, but I need the files.  I have Windows XP access on another machine (and a virtualbox on ubuntu) and an XP install CD if that helps...

Thanks,

~Ocean~


EDIT:
When I boot to the live CD, I can see the Ubuntu partition as a 68GB media, and all the files are in there, but I can't see the Vista drive.  When I go to GParted on the CD, I see the 312GB partiton outlined in red.  I had used that as swap space, and the file system is now "linux-swap."  Did that mess it up?  Its flag is still boot...

---

### Post by Pumalite on 2008-05-21
Post:
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by eagledrc on 2008-05-22
```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       39846   320055523+  82  Linux swap / Solaris
/dev/sda2           39847       48641    70645837+  83  Linux

```
Above is the sudo fdisk -l

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
# kopt=root=UUID=38e50b8e-f484-4a02-9191-e4d659129c0a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=38e50b8e-f484-4a02-9191-e4d659129c0a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=38e50b8e-f484-4a02-9191-e4d659129c0a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
Above is the cat /boot/grub/menu.lst

So basically my mistake was to refile it as linux swap space....But the data's still there, right??  I don't care as much about getting Vista up (I use Ubuntu a lot more) but I need my files...

Thanks for your help

---

### Post by Pumalite on 2008-05-22
If your files were in Vista; I'm afraid they are gone. You can take your hard drive to a Hard Drive Recovery Shop, but IS VERY EXPENSIVE.

---

### Post by eagledrc on 2008-05-22
So when you use a drive as swap space, it formats it and uses a new file system (linux-swap)?
My dad has some pros at his work that might be able to do it, but is there a good chance that they can?

Thanks,

---

### Post by Pumalite on 2008-05-22
We'll see if they are pro's

---

### Post by eagledrc on 2008-05-22
ok lol

---

### Post by Pumalite on 2008-05-22
Good luck eagledrc

---

### Post by meierfra. on 2008-05-22
Actually formating a partition as swap does not do much damage. So you should be o.k  Don't use your computer until the pros had  a look at it (everytime you use the swap partition some data will be destroyed).

 I was able to recover  an ext3 partition which was formated as swap. This it what I would do 

 ```
sudo cfdisk /dev/sda
```

and change the  type of /dev/sda1 to "7"

Then boot from a VistaCD  and run "chkdsk" from the recovery console.

Good luck.

---

### Post by eagledrc on 2008-05-27
haha too late, i already formatted it and set it up to reinstall vista....im just recreating the files that i need, its not that bad...I am planning how i am gonna back up my computer now lol

---

