---
title: "Ubuntu messed up Vista booting"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by projectgonewrong on 2008-06-05
I have a computer that came with Vista installed already.  I still wanted Vsita on this computer, so I installed Ubuntu on another hard drive so I still have all of the Vista files on one hard drive and all of the Linux files on the other hard drive.

But the problem is I installed over the boot files of Windows somehow and when I take out the Linux hard drive and try to boot off the Windows hard drive it doesn't know how to boot up because somehow I deleted those files.   So, can anyone help?  

(Also I do not know where my Vista CDs are that came with this computer)

---

### Post by Pumalite on 2008-06-05
Boot your Live CD and; from the Terminal, post:
sudo fdisk -lu

---

### Post by projectgonewrong on 2008-06-05
My friend currently has the Live CD but here's what happens on normal Ubuntu.

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3340b856

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   382122089   191061013+  83  Linux
/dev/sda2       382122090   398283479     8080695    5  Extended
/dev/sda5       382122153   398283479     8080663+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x34dc209a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    20402549    10201243+   7  HPFS/NTFS
/dev/sdb2   *    20402550   976768064   478182757+   7  HPFS/NTFS

---

### Post by VMC on 2008-06-05
Are you getting a Grub boot error when you try to boot Vista with ubuntu drive removed?

---

### Post by Pumalite on 2008-06-05
Post:
cat /boot/grub/menu.lst

---

### Post by projectgonewrong on 2008-06-05
Yes it says GRUB error 21


And here is the other cat /boot/grub/menu.lst


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
# kopt=root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro

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

title		Ubuntu 8.04, kernel 2.6.24-18-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-386

title		Ubuntu 8.04, kernel 2.6.24-18-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-18-386

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-386

title		Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-16-386

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-15-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-386

title		Ubuntu 8.04, kernel 2.6.24-15-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-15-386

title		Ubuntu 8.04, kernel 2.6.24-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu 8.04, kernel 2.6.24-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu 8.04, kernel 2.6.24-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-14-386

title		Ubuntu 8.04, kernel 2.6.24-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-14-386

title		Ubuntu 8.04, kernel 2.6.24-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu 8.04, kernel 2.6.24-12-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-386

title		Ubuntu 8.04, kernel 2.6.24-12-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-12-386

title		Ubuntu 8.04, kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 8.04, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 8.04, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 8.04, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 8.04, kernel 2.6.17-12-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386

title		Ubuntu 8.04, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.17-12-386

title		Ubuntu 8.04, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 8.04, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=2a13b955-aedb-4bb2-8a2d-55c130345792 ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Victormd on 2008-06-05
Have you tried [supergrub]("http://supergrub.forjamari.linex.org/?section=download")?

---

### Post by Pumalite on 2008-06-05
Back it up:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Edit:
gksudo gedit /boot/grub/menu.lst
Add below this line:
### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows Vista
root (hd1,0)
chainloader + 1

Save, exit, reboot.

(I hope both your drives are IDE or both SATA)

---

### Post by projectgonewrong on 2008-06-05
Okay I tried that, and it put the Windows Vista in the Boot menu but when I try to boot from that option it says "Filesystem type Unknown" so I'm guessing it's trying to boot linux but can't find the right filesystem?

---

### Post by Pumalite on 2008-06-05
Try to boot Vista with Super Grub as the poster above suggested. We'll know if Vista is still alive:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by projectgonewrong on 2008-06-05
Thank you that worked.  Well it works well enough anyways.  I have to unplug my Linux hard drive to boot Windows, but whatever I'm not going to use windows that much.

---

