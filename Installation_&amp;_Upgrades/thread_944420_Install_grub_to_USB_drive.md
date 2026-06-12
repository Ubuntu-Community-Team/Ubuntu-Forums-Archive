---
title: "Install grub to USB drive"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by texter2468 on 2008-10-11
Is it possible to install grub to a usb drive? I have a computer with xp, vista, and ubuntu on it. Currently the computer directly boots into xp and I want to keep it that way. But sometimes I need to access vista or ubuntu. Is there a way I could install grub on my USB drive to boot to one of those. 

Here is sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ce69ce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        3570    28675993+   7  HPFS/NTFS
/dev/sda3            5720        9729    32210325    5  Extended
/dev/sda4            3581        5719    17181517+   7  HPFS/NTFS
/dev/sda5            5720        9558    30836736   83  Linux
/dev/sda6            9559        9729     1373526   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by caljohnsmith on 2008-10-11
Yes, you can do that. :) I'll assume that your USB drive is "sdb", so if it isn't, be sure to change that in the following commands:
```
sudo grub
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root (hd1,4)
grub> setup (hd0)
grub> quit
```
That will install Grub to the MBR (Master Boot Record) of your external USB drive, and yet the MBR will point to your internal drive's sda5 partition for Grub's system files (menu.lst, etc). You will probably have to modify your Grub's menu.lst since you will now be booting from your USB drive.

So go ahead and boot your USB drive, and you should get the Grub menu. select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd1,Y)", press return to save the change, then press "b" to boot. That will hopefully be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to:
```
#groot=(hd1,Y)
```
Also add the following entry at the end for Windows Vista:
```
title Windows Vista
root (hd1,3)
chainloader +1

```
That should work for Vista as I've heard from others experience that Vista doesn't require using Grub's "mapping" technique like Windows XP does when booting XP from a drive other than the boot drive. But if it doesn't work, let me know. Anyway, save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems. :)

---

### Post by texter2468 on 2008-10-11
It did not work completely. Ubuntu and XP boot fine, but when I try to boot vista I get the error "a disk read error has occurred. Press ctrl+alt+del to restart"

Here is sudo fdisk -l and my menu.lst file.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ce69ce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        3570    28675993+   7  HPFS/NTFS
/dev/sda3            5720        9729    32210325    5  Extended
/dev/sda4            3581        5719    17181517+   7  HPFS/NTFS
/dev/sda5            5720        9558    30836736   83  Linux
/dev/sda6            9559        9729     1373526   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 65 MB, 65208320 bytes
255 heads, 63 sectors/track, 7 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000fc8e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           8       63648+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(6, 254, 63) logical=(7, 236, 37)

```

```

user1@user1-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title Windows Vista
root (hd1,3)
chainloader +1

```

---

### Post by caljohnsmith on 2008-10-11
Are you sure you are able to boot into XP from the Grub menu? The menu.lst entry for XP uses (hd0,1), which can't be correct since XP is on the same drive as Ubuntu; therefore it should use (hd1,1). Also, to boot XP from a drive other than the boot drive, you have to use Grub's mapping technique:
```
title	   Windows XP
root       (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Also, go ahead and replace the Vista entry with:
```
title	   Windows Vista
root       (hd1,3)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And see if that makes any difference. You might still have some issues with Vista that you'll have to fix to get it booting properly again.

---

### Post by texter2468 on 2008-10-12
> **caljohnsmith said:**
> Are you sure you are able to boot into XP from the Grub menu? The menu.lst entry for XP uses (hd0,1), which can't be correct since XP is on the same drive as Ubuntu; therefore it should use (hd1,1). Also, to boot XP from a drive other than the boot drive, you have to use Grub's mapping technique:
```
title	   Windows XP
root       (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Also, go ahead and replace the Vista entry with:
```
title	   Windows Vista
root       (hd1,3)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And see if that makes any difference. You might still have some issues with Vista that you'll have to fix to get it booting properly again.
Yes it was booting xp, but it may have been defaulting and booting directly from my hard drive. I have made the changes you told me to, but now I get the error "ntldr is missing press ctrl+alt+del to restart" when I try to boot vista. Xp and Ubuntu are booting fine.

Here is my menu.lst again

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
# kopt=root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c9d588d4-9dd5-4c8e-8b60-54e606bdd50f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title	   Windows XP
root       (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows Vista
root       (hd1,3)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```

---

### Post by meierfra. on 2008-10-12
> ntldr is missing press ctrl+alt+del to restart"

This means that you still have the XP-style boot sector installed in /dev/sda4.

Did you do

```
e:\boot\bootsect.exe /nt60 X: 
```

---

### Post by texter2468 on 2008-10-12
> **meierfra. said:**
> This means that you still have the XP-style boot sector installed in /dev/sda4.

Did you do

```
e:\boot\bootsect.exe /nt60 X: 
```
Yes I did. Where x is the vista drive letter right?

---

### Post by meierfra. on 2008-10-12
> Where x is the vista drive letter right?

Yes.  Did you get any error message after "e:\boot\bootsect.exe /nt60 X" ?

(also "e:" needs to be the drive letter for your CDrom drive)

You also might boot from the Vista CD and run

```
bootrec /fixboot
```

---

### Post by texter2468 on 2008-10-12
Thanks. I was doing it wrong. Everything is booting fine now. Thanks for both your help. Also one last question. How would I put this grub configuration on another memory key in case I loose the memory key I currently am using?

---

### Post by caljohnsmith on 2008-10-12
When you say memory key, do you mean another USB drive? If so you could follow the first steps in post #2 to install Grub to the MBR of your new USB drive, or you could use the "dd" command to copy the MBR over; I would recommend just using the grub steps from post #2 though.

---

### Post by texter2468 on 2008-10-13
That's what I'll do thanks!

---

