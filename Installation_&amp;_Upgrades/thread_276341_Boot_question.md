---
title: "Boot question"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by smurf0 on 2006-10-12
I have 2 disks on my pc:

- an ide on secondary master with Ubuntu
- a windows XP professional on a sata hdd

I can select on my bios the hard disk to boot first but I'd like to configure grub or windows boot.ini

Wich is the most simple to configure?
How can I do this operation?

PS: sorry for my english, I'm Italian... And sorry if i posted in the wrong section

---

### Post by Kateikyoushi on 2006-10-12
I would recommend to use grub instead of the windows bootloader.

[Here is a guide to the install.]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by smurf0 on 2006-10-12
With that guide I can add windows boot from grub?

---

### Post by randell6564 on 2006-10-12
> **Kateikyoushi said:**
> I would recommend to use grub instead of the windows bootloader.

[Here is a guide to the install.]("http://doc.gwos.org/index.php/Restore_Grub")
Thats a good idea EXCEPT.,Ubuntu might not recognize the [S-ATA device]("http://linuxmafia.com/faq/Hardware/sata.html") and instead install GRUB onto the IDE which will fail to dual-boot!

---

### Post by confused57 on 2006-10-13
> **smurf0 said:**
> With that guide I can add windows boot from grub?
If I understand correctly, you're using bios to boot into Ubuntu or Windows...you'll probably need to add an entry to boot Windows similar to this:

```
title              Windows XP Professional
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

In Ubuntu, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L"

then

```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list, not menu.first

Post the output of the above commands, for menu.lst you can just post the entries for booting Ubuntu.  Someone can probably help you with this information.

---

### Post by smurf0 on 2006-10-13
This is my output:

smurf@smurf-ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26519   213013836    7  HPFS/NTFS
/dev/sda2   *       26520       36483    80035798+   7  HPFS/NTFS

Disk /dev/hdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3497    28089621   83  Linux
/dev/hdc2            3498        3649     1220940    5  Esteso
/dev/hdc5            3498        3649     1220908+  82  Linux swap / Solaris
smurf@smurf-ubuntu:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hdc1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
smurf@smurf-ubuntu:~$

---

### Post by confused57 on 2006-10-13
You might be able to add a Windows entry similar to the one I gave you in my last reply...see this guide for how to edit grub:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Ignore the parts about disconnecting drives, since you already have Ubuntu installed...mainly check out the commands for adding the Windows entry.
From your **fdisk -l**, it looks like your root may be (hd1,1), if not, try (hd1,0).

---

### Post by smurf0 on 2006-10-13
> **confused57 said:**
> You might be able to add a Windows entry similar to the one I gave you in my last reply...see this guide for how to edit grub:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Ignore the parts about disconnecting drives, since you already have Ubuntu installed...mainly check out the commands for adding the Windows entry.
From your **fdisk -l**, it looks like your root may be (hd1,1), if not, try (hd1,0).

You are great! It wotks with (hd1,1), thank you very much!!!!:-D

---

