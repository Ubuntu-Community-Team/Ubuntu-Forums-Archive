---
title: "Dual boot goes straight into XP"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by mikegeig on 2008-09-06
Hello, I am trying to get a dual boot system running. I started with XP installed in a 250gb drive. I resized the drive to 125gb pairs and installed ubuntu on the 2nd partition. When the computer boots, it goes directly into XP. I have tried many different solutions with no success. I have tried booting from the live CD and running grub from the terminal. When I type "setup (hd0)" I get a mounting error. When I try "find /boot/grub/stage1" I get an error "file not found". What can I do?

Thank you

---

### Post by Pumalite on 2008-09-06
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by mikegeig on 2008-09-06
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0febe7da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   240107489   120053713+  42  SFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0febe7da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   240107489   120053713+  42  SFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8ff88ff8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   241890704   120945321    7  HPFS/NTFS
/dev/sdd2       241890705   488392064   123250680    5  Extended
/dev/sdd5       241890768   253602089     5855661   82  Linux swap / Solaris
/dev/sdd6       253602153   488392064   117394956   83  Linux
ubuntu@ubuntu:~$

---

### Post by mikegeig on 2008-09-06
Perhaps I do not understand what is required to make grub work, or where it needs to be placed. When I installed Ubuntu, I checked to put it in hd0 (default). Is it possible that I put it in the wrong place (since XP is partitions 1, with the linux partitions following)?

---

### Post by Sef on 2008-09-06
From the GRUB Manual:

> **14.1 Errors reported by the Stage 1**

  The general way that the Stage 1 handles errors is to print an error string and then halt. Pressing <CTRL>-<ALT>-<DEL> will reboot.     
The following is a comprehensive list of error messages for the Stage 1:       
Hard Disk ErrorThe stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed.       
Floppy ErrorThe stage2 or stage1.5 is being read from a floppy disk, and the attempt to determine the size and geometry of the floppy disk failed. It's listed as a separate error since the probe sequence is different than for hard disks.       
Read ErrorA disk read error happened while trying to read the stage2 or stage1.5.       
Geom ErrorThe location of the stage2 or stage1.5 is not in the portion of the disk supported directly by the BIOS read calls.  This could occur because the BIOS translated geometry has been changed by the user or the disk is moved to another machine or controller after installation, or GRUB was not installed using itself (if it was, the Stage 2 version of this error would have been seen during that process and it would not have completed the install).  

Have you tried reinstalling grub with the [Super GRUB Disk]("http://www.supergrubdisk.org/")?

---

### Post by Pumalite on 2008-09-06
Is sdd an external drive? What happened to sdc? What do you have in sda and sdb?

---

### Post by caljohnsmith on 2008-09-06
> **mikegeig said:**
> Perhaps I do not understand what is required to make grub work, or where it needs to be placed. When I installed Ubuntu, I checked to put it in hd0 (default). Is it possible that I put it in the wrong place (since XP is partitions 1, with the linux partitions following)?
Which HDD are you booting off of on start up? Because that HDD will be where Grub is installed in the master boot record (MBR), since you had grub install to (hd0). 

From the Live CD, please try the following:
```
sudo mount /dev/sdd6 /mnt
ls -lR /mnt/boot
cat /mnt/boot/grub/menu.lst
```

---

### Post by mikegeig on 2008-09-06
> **caljohnsmith said:**
> Which HDD are you booting off of on start up? Because that HDD will be where Grub is installed in the master boot record (MBR), since you had grub install to (hd0). 

From the Live CD, please try the following:
```
sudo mount /dev/sdd6 /mnt
ls -lR /mnt/boot
cat /mnt/boot/grub/menu.lst
```

Well, I can run those 3 commands. The last command gives me what would appear to be a list of what GRUB should say upon loading: 

ubuntu
ubuntu (recovery mode)
other:
windows XP

What does this mean exactly? The delve into my setup a little more, I have XP and ubuntu installed on an IDE drive, then I have a mirrored sata raid that is blank right now.Also, XP is listed as "savedefault", "makeactive" and also as (hd2,0). While ubuntu is (hd2,5). 

Does this help?

---

### Post by mikegeig on 2008-09-06
the command: 

```
sudo grub-install /dev/hda 
```

returns "/dev/hda not found or not a block device"

---

### Post by falcon61102 on 2008-09-06
Could you post a copy of your menu.lst here so that we can see it?

Also, could you post the results of the following:
```
sudo blkid
```
That will give you the UUID's for all your partitions which sometime get all mixed up in the GRUB.

---

### Post by Pumalite on 2008-09-06
Check the results of blkid against /etc/fstab and menu.lst

---

### Post by mikegeig on 2008-09-06
blkid:

/dev/sda1: UUID="381C5C211C5BD888" LABEL="Backup" TYPE="ntfs" 
/dev/sdb1: UUID="381C5C211C5BD888" LABEL="Backup" TYPE="ntfs" 
/dev/sdc1: UUID="EE4401034400CFEF" TYPE="ntfs" 
/dev/sdc5: UUID="f7371808-9e21-4f39-b34c-6b3031ba2aad" TYPE="swap" 
/dev/sdc6: UUID="125808aa-07a8-451a-b18b-fa6e5237dc9a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 


Also, where is menu.lst so I can output it?

---

### Post by falcon61102 on 2008-09-06
It's in /boot/grub of your root partition.

---

### Post by mikegeig on 2008-09-06
Here is my menu.lst

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
# kopt=root=UUID=a2b4f739-0127-4539-8935-8c2617ccd12b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a2b4f739-0127-4539-8935-8c2617ccd12b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a2b4f739-0127-4539-8935-8c2617ccd12b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by falcon61102 on 2008-09-06
If you look in at the output of your blkid command you'll see that the UUID for sdc6 does not match the menu.lst.  If you copy the UUID from the blkid output to the menu.lst and replace the UUID's in both kernal strings then you should be good to go.

---

