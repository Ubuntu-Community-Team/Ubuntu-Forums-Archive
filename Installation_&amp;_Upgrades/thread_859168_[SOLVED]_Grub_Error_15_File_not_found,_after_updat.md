---
title: "[SOLVED] Grub: Error 15 File not found, after updates in new 8.04 install"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by Dr Bones on 2008-07-14
Ok,
  
I installed 8.04 on some new hardware, as I built a new computer and wanted to transfer some of the files I had on the previous hardy install to this machine. I chose to have the new installation of hardy use the entire sda hard drive (see the output and following terminal outputs as a reference of how the drives are setup).  

Here is a little information about the hardware I have connected to the machine.  I have a total of 4 physical hard drives on this computer, one of which is only connected in order for me to transfer the data from an older installation of 8.04 I was using before my new build and will be removed after I sort out the problems I am having.  2 of the other drives installed will be eventually set up into a software raid 1 disk, that I can use as a long term data backup and storage drive when I have the time.  Here is the output when I run sudo fdisk -l

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89722   720691933+  83  Linux
/dev/sda2           89723       91201    11880067+   5  Extended
/dev/sda5           89723       91201    11880036   82  Linux swap / Solaris

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00083dc0

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        9729    78148161   83  Linux

Disk /dev/hdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d253b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1        9729    78148161   83  Linux

Disk /dev/hdg: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b047c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1       14218   114206053+  83  Linux
/dev/hdg2           14219       14593     3012187+   5  Extended
/dev/hdg5           14219       14593     3012156   82  Linux swap / Solaris

```

hde and hdf are the 2 drives, which I would like to have setup in a software raid setup in the future, sda is the main hardisk I have and hdg is the hard drive from the previous installation which I am going to be giving to a friend once I settle the problems I am having.  Here is the output for cat /boot/grub/menu.lst run in a terminal

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
# kopt=root=UUID=7eae37c8-6940-4f82-ba71-960f20024517 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eae37c8-6940-4f82-ba71-960f20024517 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eae37c8-6940-4f82-ba71-960f20024517 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7eae37c8-6940-4f82-ba71-960f20024517 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7eae37c8-6940-4f82-ba71-960f20024517 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-18-generic (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro single 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-17-generic (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro single 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-11-generic (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-11-generic (recovery mode) (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro single 
initrd		/boot/initrd.img-2.6.24-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-8-generic (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-8-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, kernel 2.6.24-8-generic (recovery mode) (on /dev/hde1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=024dacce-d23a-4409-8d32-8ba5d1866248 ro single 
initrd		/boot/initrd.img-2.6.24-8-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hde1.
title		Ubuntu 8.04, memtest86+ (on /dev/hde1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```


As for the install I have setup on the sda hard drive, I ran all the updates and the kernel was upgraded to 2.6.24-19.  I chose this option in grub after I restarted my computer (told me a manditory restart was required) and I was given an error 15: File not found.  I am wondering why this is error is showing up and or what I would have to do in order to remedy this problem.  On another note the boot option for 2.6.24-16 generic does work from the grub menu and is what I have been using since as I still cannot get the -19 boot to work.  I really would like to be running the latest kernel but if I have to stick to -16 that would be fine as well.

After I had setup compiz and the desktop backgrounds and various other settings how I liked them and transferred the files off of hdg I removed it and restarted the computer.  I selected the 2.6.24-16 option as I had been accustomed to in order to get the system to boot and I recieved the same error; Error 15 file not found as I had been seeing with the -19 option.  I tried running both of the recovery options, -16 and -19 and neither of them worked.  I reconnected hdg and I was again able to boot leading me to believe that the boot I was successfully able to boot to was on the disk I desire to remove.  Looking at the output of "cat /boot/grub/menu.lst" in a terminal I was under the assumption that both of those installs should be linked to hard drive sda.  I was wondering if anyone could point out where I appear to be going wrong and what I can do in order to remedy the situation.  Thank you in advance and ask if you need me to give you any more info.

---

### Post by mikewhatever on 2008-07-14
In the GRUB menu, all kernel entries from -16 to -18 are on (hd0,0), whereas -19 is the only one on (hd1,0). Try changing that to hd0 and see what happens.

---

### Post by Dr Bones on 2008-07-14
I made the suggested change and it did indeed work.  Thank you, sometimes the most blatant things are often overlooked.

---

