---
title: "Windows XP does not boot with Ubuntu 8.04"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by jgag123 on 2008-07-03
Hi everyone.
I've been using Ubuntu 7.04, than 7.10 for about a year by now, dual boot with windows xp on separate hard drive.
Now I just downloaded the Ubuntu 8.04 and installed it, but it never gave me the option to import any documents and favorites from the windows xp that is on the other hdd, and after installation at start up it does not give me the option to boot to windows xp.The Ubuntu 7.04 and7.10 did.
How do I boot in to windows xp?

Thanks  in advance

---

### Post by allarmguy on 2008-07-03
If you cut the disk with ubuntu you can boot xp?
Then you can try using WUBI and reinstall ubuntu.This I`m sure it works because I do that

---

### Post by confused57 on 2008-07-03
> **jgag123 said:**
> Hi everyone.
I've been using Ubuntu 7.04, than 7.10 for about a year by now, dual boot with windows xp on separate hard drive.
Now I just downloaded the Ubuntu 8.04 and installed it, but it never gave me the option to import any documents and favorites from the windows xp that is on the other hdd, and after installation at start up it does not give me the option to boot to windows xp.The Ubuntu 7.04 and7.10 did.
How do I boot in to windows xp?

Thanks  in advance
I'm sure someone can help you if you can post the output of:
```
sudo fdisk -l
```
-l is a small "L"
and
```
gedit /boot/grub/menu.lst
```

---

### Post by mvdberg112 on 2008-07-03
Check also these:
[http://ubuntuforums.org/showthread.php?t=255053]("http://ubuntuforums.org/showthread.php?t=255053")
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
it seems that 8.04 did not take over your menu.lst from 7.10
Please, can you tell: did you do an upgrade or a complete new installation?

---

### Post by jgag123 on 2008-07-03
I did a new install. This is what I get:

j@j-desktop:~$ sudo fdisk -l
[sudo] password for j: 

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008fbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070    5  Extended
/dev/sda5            3494        3649     1253038+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00630062

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS
j@j-desktop:~$

---

### Post by jgag123 on 2008-07-03
Than this is for the second search:

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
# kopt=root=UUID=c3a977dc-48c7-430a-8169-2e98bf2b1a18 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c3a977dc-48c7-430a-8169-2e98bf2b1a18 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c3a977dc-48c7-430a-8169-2e98bf2b1a18 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c3a977dc-48c7-430a-8169-2e98bf2b1a18 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c3a977dc-48c7-430a-8169-2e98bf2b1a18 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

I no not much about commands.

Thanks

---

### Post by confused57 on 2008-07-03
Open a terminal, copy & paste one line at a time:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Copy & paste this Windows entry at the VERY END of your menu.lst:
```
title  Windows XP    
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

Quit & Save.  Note:  You can put anything you like after the word title to make it more descriptive.

---

### Post by jgag123 on 2008-07-04
> **confused57 said:**
> Open a terminal, copy & paste one line at a time:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Copy & paste this Windows entry at the VERY END of your menu.lst:
```
title  Windows XP    
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

Quit & Save.  Note:  You can put anything you like after the word title to make it more descriptive.

Ok, what is this suppose to do. I have done it the way you said but did not make any different in booting. I still can not get in to Windows XP.

Thanks

---

### Post by jgag123 on 2008-07-04
What if I reinstall Windows XP and then Ubuntu 8.04 (even if I don't really want to). Would it give me the option to copy documents and favorites and would it give me the option to boot either Windows or Ubuntu? 
Or the Ubuntu 8.04 is not suppose to do that? 7.10 did that.

Thanks

---

### Post by confused57 on 2008-07-04
You could try Super Grub Disk to boot your Windows drive:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Do you get any error messages or does Windows try to boot when you use the Window's entry I gave you?

---

### Post by studyhard888 on 2008-07-04
[FONT="Verdana"][/FONT][SIZE="4"][/SIZE][COLOR="Blue"][/COLOR]
that you just modify the boot menu is ok .
but most curious to me is that ubuntu 8.04 will not alter ur boot menu .
i update the ubuntu flawlessly

---

