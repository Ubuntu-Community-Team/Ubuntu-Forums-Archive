---
title: "upgrade failed error 21 : selected disk doesn't exists"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by senectus on 2008-10-27
I ran an inplace upgrade and though it looks like it mostly worked it refuses to use the 8.10 kernels...
If I select one of those kernels in the grub menu I get a message that says:

Error 21 : Selected disk does not exist

Does anyone know what this means?

(btw I upgraded using update-manager -d from 8.04)

---

### Post by lemming465 on 2008-10-28
Can we see the output from "cat /etc/fstab; cat /boot/grub/menu.lst; df -m"?  The message sounds like there is an issue with either identifying the boot partition for grub or the root partition for the kernel.  How many disks are in the machine, and what kind? (IDE? SATA? SCSI? USB?)

---

### Post by senectus on 2008-10-29
> cat /etc/fstab; cat /boot/grub/menu.lst; df -m
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=880bdb82-0b89-4bb9-ac67-e743382b550d /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=a723cc11-e1dd-4b96-bea7-9e6ac6a587bd none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
default 0
timeout 10

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.24-16-386
quiet

title Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.24-16-386

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.24-15-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-15-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.24-15-386
quiet

title Ubuntu 8.04, kernel 2.6.24-15-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-15-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.24-15-386

title Ubuntu 8.04, kernel 2.6.24-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-15-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.24-15-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-15-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-15-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.24-15-generic

title Ubuntu 8.04, kernel 2.6.24-14-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-14-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.24-14-386
quiet

title Ubuntu 8.04, kernel 2.6.24-14-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-14-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.24-14-386

title Ubuntu 8.04, kernel 2.6.24-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-14-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.24-14-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-14-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.24-14-generic

title Ubuntu 8.04, kernel 2.6.24-12-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-12-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.24-12-386
quiet

title Ubuntu 8.04, kernel 2.6.24-12-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-12-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.24-12-386

title Ubuntu 8.04, kernel 2.6.24-12-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.24-12-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.24-12-generic

title Ubuntu 8.04, kernel 2.6.22-14-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.22-14-386
quiet

title Ubuntu 8.04, kernel 2.6.22-14-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.22-14-386

title Ubuntu 8.04, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Ubuntu, kernel 2.6.20-16-lowlatency (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-lowlatency
savedefault

title Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.20-16-lowlatency
savedefault

title Ubuntu, kernel 2.6.20-16-generic (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.20-16-generic
savedefault

title Ubuntu, kernel 2.6.20-15-generic (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.20-15-generic
savedefault

title Ubuntu, kernel 2.6.17-10-386 (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-386 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-386
savedefault

title Ubuntu, kernel 2.6.17-10-386 (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-386 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.17-10-386
savedefault

title Ubuntu, kernel 2.6.17-10-generic (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
savedefault

title Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.17-10-generic
savedefault

title Ubuntu, kernel 2.6.15-27-k7 (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-27-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-k7
savedefault

title Ubuntu, kernel 2.6.15-27-k7 (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-27-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.15-27-k7
savedefault

title Ubuntu, kernel 2.6.15-26-k7 (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-26-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-k7
savedefault

title Ubuntu, kernel 2.6.15-26-k7 (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-26-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.15-26-k7
savedefault

title Ubuntu, kernel 2.6.15-25-k7 (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-25-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.15-25-k7
savedefault

title Ubuntu, kernel 2.6.15-25-k7 (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-25-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.15-25-k7
savedefault

title Ubuntu, kernel 2.6.15-23-k7 (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-23-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-k7
savedefault

title Ubuntu, kernel 2.6.15-23-k7 (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-23-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.15-23-k7
savedefault

title Ubuntu, kernel 2.6.15-23-686 (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-23-686 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-686
savedefault

title Ubuntu, kernel 2.6.15-23-686 (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-23-686 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.15-23-686
savedefault

title Ubuntu, kernel 2.6.15-17-k7 (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-17-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.6.15-17-k7
savedefault

title Ubuntu, kernel 2.6.15-17-k7 (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-17-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.6.15-17-k7
savedefault

title Ubuntu, kernel 2.4.27-2-k7 (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.4.27-2-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro quiet splash
initrd /boot/initrd.img-2.4.27-2-k7
savedefault

title Ubuntu, kernel 2.4.27-2-k7 (recovery mode) (on /dev/hdb2)
root (hd1,1)
kernel /boot/vmlinuz-2.4.27-2-k7 root=UUID=577c5722-8919-4cef-b37d-5630cf380b84 ro single
initrd /boot/initrd.img-2.4.27-2-k7
savedefault

title Ubuntu, memtest86+ (on /dev/hdb2)
root (hd1,1)
kernel /boot/memtest86+.bin
savedefault
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
# kopt=root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.10, kernel 2.6.22-14-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-386
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro  single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=880bdb82-0b89-4bb9-ac67-e743382b550d ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
Filesystem           1M-blocks Used Available Use% Mounted on
/dev/sda1               184875    160667     14817  92% /
tmpfs                      505         0       505   0% /lib/init/rw
varrun                     505         1       505   1% /var/run
varlock                    505         0       505   0% /var/lock
udev                       505         3       502   1% /dev
tmpfs                      505         1       505   1% /dev/shm
lrm                        505         2       503   1% /lib/modules/2.6.27-7-generic/volatile


It looks like it's pointing to the wrong partition?!?!

---

### Post by caljohnsmith on 2008-10-29
My gosh I've never seen a menu.lst with so many kernels listed. Have you considered maybe uninstalling some of your older kernels? You can do it in Synaptic Package Manager. 

Your old Hardy entries use (hd0,0), while your new Intrepid entries use (hd2,0); probably if you change the (hd2,0) to (hd0,0) you can boot the Intrepid entries. If that doesn't work, how about posting:
```
sudo fdisk -lu
sudo blkid
ls -l /boot
```
Let me know how it goes.

---

### Post by lemming465 on 2008-10-30
With intrepid removing obsolete kernels got easier than hunting them down in synaptic.  Try the new "Cruft Remover" tool; I love it.

---

