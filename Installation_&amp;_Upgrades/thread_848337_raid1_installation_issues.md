---
title: "raid1 installation issues"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by mikerd on 2008-07-03
Hello,

I'm setting up software raid on a new install.  Followed a number of tutorials to set-up raid1 via Ubuntu Server CD.  All goes well, boots fine.  Then I go into grub to install grub bl on the second disk.  Keep getting error 15.

*device (hd0) /dev/sda*

Error 15: File not Found

*root (hd0,0)*

Error 15: File not Found

Mdstat seems to indicate all is well.  

My setup is pretty simple:
Ubuntu Server 8.04
2 500GB SATA Hard Disks
No Hardware Raid Controller
4 RAID1 set-up during Ubuntu Install
md0 /
md1 /tmp
md2 /var/log
md3 swap

I'm returning to linux after a number of years, so I'm rusty.  Could be something silly I'm missing. 

Any help??


More info:

 cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=6d3e2ab0-d461-421a-b12c-c7ed28ea4827 /               ext3    relatime,error
s=remount-ro 0       1
# /dev/md1
UUID=209cbb3e-ed65-4dcc-ad2f-caf8e182e3d6 /tmp            ext3    relatime      
  0       2
# /dev/md3
UUID=08575966-4f80-4bbc-98eb-92418c8e2a35 /var/log        ext3    relatime      
  0       2
# /dev/md2
UUID=f9fa2a89-d757-4910-a994-675630eae2f1 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by mikerd on 2008-07-04
More info...  Anyone who might be able to help??

cat /boot/grub/menu.lst
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
# kopt=root=/dev/md0 ro

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
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=/dev/md0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=/dev/md0 ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.1, kernel 2.6.24-16-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-server root=/dev/md0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-server root=/dev/md0 ro single
initrd		/boot/initrd.img-2.6.24-16-server

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by woland on 2008-07-19
mikerd, did you manage to solve this issue?

I have a similar one, I have set up RAID 1 on two 250GB PATA drives and did not succeed on setting grub on the second drive to make them both bootable.
I get the same "Error 15" when I enter the same commands.

I've used [this guide]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") to make the RAID array.

---

