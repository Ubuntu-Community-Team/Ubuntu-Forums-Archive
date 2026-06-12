---
title: "[SOLVED] ubuntu grub problem"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by vinu76jsr on 2008-06-11
I have installed windows on my system in 20 GB partition and ubuntu in 50 gb partition they both are in same hard disk and I have separate hard disk which is used simply for storage
My fdisk -l output is

```
vaibhav@vrindavan:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17e917e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3de2a9a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6566    52741363+  83  Linux
/dev/sdb2            6567        6787     1775182+  82  Linux swap / Solaris
/dev/sdb3            6788        9728    23623582+   7  HPFS/NTFS

```

I have first installed ubuntu and then windows
now I am not able to figure out how to configure grub for windows boot my /boot/grub/menu.lst file is 
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=7be43d00-e3fe-45b0-9121-a440b18cbd56 ro

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
# howmany=1

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7be43d00-e3fe-45b0-9121-a440b18cbd56 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7be43d00-e3fe-45b0-9121-a440b18cbd56 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title		Windows XP
root		(hd0,0)
savedefault	
makeactive	
chainloader	+1

```

the last windows entry is entered by me which show a error like unrecognised executables

my windows installation is perfectly fine please help

---

### Post by Partyboi2 on 2008-06-11
You can boot the ubuntu live cd and use that to restore grub.
[[COLOR=Blue]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") is a how-to

---

### Post by Herman on 2008-06-11
Hello vinu76jsr
Try changing your Windows entry's 'root' line from (hd0,0) to (hd0,2), because Windows is in your third partition.    
        
```
### END DEBIAN AUTOMAGIC KERNELS LIST
title        Windows XP
root        (hd0,2)
savedefault    
makeactive    
chainloader    +1
```

---

### Post by vinu76jsr on 2008-06-11
> **Herman said:**
> Hello vinu76jsr
Try changing your Windows entry's 'root' line from (hd0,0) to (hd0,2), because Windows is in your third partition.    
        
```
### END DEBIAN AUTOMAGIC KERNELS LIST
title        Windows XP
root        (hd0,2)
savedefault    
makeactive    
chainloader    +1
```
I really appreciate your suggestion and it worked for me 
Thanx

---

