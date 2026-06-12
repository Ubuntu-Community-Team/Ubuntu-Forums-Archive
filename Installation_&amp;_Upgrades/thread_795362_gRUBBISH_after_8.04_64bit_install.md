---
title: "gRUBBISH after 8.04 64bit install"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by 4partee on 2008-05-15
I just got the (Error 15: file not found) on the initial boot after installing 8.04.

My system has 3 HDDs and one DVD; IDE0 Primary, SATA0 Primary, SATA0 Secondary and the DVD is SATA1 Primary as reported by BIOS.

I would have liked to leave the IDE0 drive alone as it is a pure Windows drive with a Windows MBR. 

 In 7.04 the drives were hda, sda, and sdb where sda is the 7.04 installation. I have been running 7.04 from the drive that 8.04 now calls the sdb.  

The 8.04 install reported the HDDs as sda, sdb, and sdc, which I assumed to be hd(n) 0,1 and 2 to grub.  I installed 8.04 on sdc using guided, entire disk and used the advanced button to select sdc instead of hd(0) as there was no hd(2) choice!!!???. 

The installation completed without any problem until the reboot.  Before the reboot, I changed the BIOS to boot from SATA0 Secondary. The grub menu looked ok but I could not boot 8.04 or 7.04. 

I am typing this on a different computer and as soon as I restore the target computer BIOS to boot from SATA0 Primary again, I will follow up with any info that is requested.

Thank you
John

---

### Post by 4partee on 2008-05-15
...cont'd:

device.map 
#8.04
#motherboard ID, 	BIOS ID
#IDE1 Master, 		IDE0 Primary
(hd0)	/dev/sda
#SATA1, 		SATA0 Primary
(hd1)	/dev/sdb
#SATA2, 		SATA0 Secondary
(hd2)	/dev/sdc

menu.lst (all I added is the comment in the first line, otherwise exactly as installed)
##@ 8.04 2008-05-15
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
# kopt=root=UUID=5aaa36f7-a9c7-4150-8584-d5481b08afe4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5aaa36f7-a9c7-4150-8584-d5481b08afe4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5aaa36f7-a9c7-4150-8584-d5481b08afe4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=606e92ab-1c05-4529-89d9-7b4be7ad6fb8 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=606e92ab-1c05-4529-89d9-7b4be7ad6fb8 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=606e92ab-1c05-4529-89d9-7b4be7ad6fb8 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=606e92ab-1c05-4529-89d9-7b4be7ad6fb8 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by Rallg on 2008-05-15
Try this: When Grub appears, manually edit the menu line for whatever you want to boot. Specifically, you want to try changing the root hard drive location. If the menu normally says (hd2,0) then try (hd1,0) or whatever.

The change is temporary (not saved in menu.lst).

The worst that will happen is that you'll either boot into the wrong operating system, or not boot. It won't wreck your installation.

If by chance you find a combination that works, then you can manually edit menu.lst.

I won't guarantee that the above will solve your problem, but it's easy to try.

---

### Post by 4partee on 2008-05-15
Thanks Rallg.

I'm sorry but I forgot to ask a question!!

I'm not looking for a solution so much as wanting to know what I did wrong. 

IOW, if I did everything right, I would like to report this on launchpad so the developers can correct the installer.

John

---

### Post by 4partee on 2008-05-18
...cont'd

Searching launchpad revealed this to be a known problem.

[https://bugs.launchpad.net/ubuntu/+bug/223994](https://bugs.launchpad.net/ubuntu/+bug/223994)

and

[http://ubuntuforums.org/showthread.php?t=731401](http://ubuntuforums.org/showthread.php?t=731401)

I booted the 8.04 install cd.  Fdisk -l reported the IDE0 as sdc whereas the installer reported the IDE0 as sda.

The only way I can see proceed is to migrate off of the IDE0 and not mix sata and pata.

John

---

### Post by Pumalite on 2008-05-18
You got it! All SATA or all IDE.

---

### Post by 4partee on 2008-09-20
Update:

There has been some progress in that the 64bit kernel has stopped randomizing device ids.

However, there is another speedbump where the kernel updates change (hdx,y) values:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/211455](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/211455)

The developers have erroneously(IMHO) classified this as a duplicate of the randomizing bug.

EDIT:

Well, it looks like I am wrong in that the randomizing continues.
Yesterday, 2008-09-19, my devices were:
root@voyager:/boot/grub# fdisk -l|grep Disk
Disk /dev/sda: 120.0 GB, 120034123776 bytes   <---------IDE0 100% Windows
Disk identifier: 0xc8e067c5
Disk /dev/sdb: 500.1 GB, 500107862016 bytes   <---------SATA0 U8.04
Disk identifier: 0x94759475
Disk /dev/sdc: 500.1 GB, 500107862016 bytes   <---------SATA1 U7.04
Disk identifier: 0x00027610

...and today, 2008-09-20, after a cold boot my devices are:
root@voyager:/boot/grub# fdisk -l|grep Disk
Disk /dev/sda: 500.1 GB, 500107862016 bytes   <---------SATA0 U8.04 BIOS boot drive, was sdb
Disk identifier: 0x94759475
Disk /dev/sdb: 500.1 GB, 500107862016 bytes   <---------SATA1 U7.04 , was sdc
Disk identifier: 0x00027610
Disk /dev/sdc: 120.0 GB, 120034123776 bytes   <---------IDE0 100% Windows, was sda
Disk identifier: 0xc8e067c5
root@voyager:/boot/grub# 

My BIOS boot drive is SATA0=U8.04.  

I don't understand why I am experiencing this randomization since this bug [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497) is status 'Fix Released'!?!?!?!

HTH;
John

---

