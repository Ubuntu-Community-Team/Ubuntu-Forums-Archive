---
title: "install XP dual boot"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by mvdberg112 on 2008-06-21
I have Ubuntu 7.10 (going to be upgraded to 8.04).
How can I install XP, and still have dual boot?

Is there a concise about how to have different partitions with differnt bootmanagers?

Did search on 'dual boot XP'  but found not helpful info. When I have success, I will post want I did and how for the folks after me.

Thanks in advance!
Michael

---

### Post by mvdberg112 on 2008-07-01
any suggestions?

---

### Post by Pumalite on 2008-07-01
Just make space for XP, format ntfs, install XP, and then reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Later edit /etc/menu.lst and add XP

---

### Post by Phixion on 2008-07-01
If you're new at this it would be easier to install Windows XP first, then create a new partition for Ubuntu and install.


GRUB will then auto detect Windows and Linux and ask you what you want to boot into.

---

### Post by mvdberg112 on 2008-07-03
Double Thanks.
> **Phixion]...easier to install Windows XP first, then ... Ubuntu...
GRUB will then auto detect Windows...[/quote]
Yes, it would have been more clever to install Win first, but I lost the CD and found it now.
[QUOTE=Pumalite said:**
> Just make space for XP, format ntfs, install XP, and then reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
**Later edit /etc/menu.lst and add XP**I still wondered how to add XP. Is there a standard line for it? This link gives more info: [http://ubuntuforums.org/showthread.php?t=255053]("http://ubuntuforums.org/showthread.php?t=255053")
It's a bit strange that there does not seem to be a standard instruction how booting of other OSs work. Or is it just 'chainload' and then it will find itself?

I found different suggestions in both threats and copy four of them.
Which options are optional and which are the real key?
*I understand that: root or rootnoverify set the right partition
*what does **chainloader +1** exactly do? why **+1**?
*when is **makeactive** required?
```
title        Microsoft Windows 9x & XP Professional
rootnoverify (hd0,4)
chainloader    +1
boot

title        Microsoft Windows XP Professional
root        (hd0,4)
savedefault
makeactive
chainloader    +1

# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1

title Windows 2000
root (hd0,0)
savedefault
#makeactive
chainloader +1
```PS: one of the threats also mentions that the boot.ini in Windows needs to be correct. This starts playing a role after Grub has selected the right OS and handed over the control to the OS's bootloader. Not a Linux problem, but critical.

---

### Post by Pumalite on 2008-07-03
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by mvdberg112 on 2008-07-03
> **Pumalite said:**
> Post:
sudo fdisk -lu
cat /boot/grub/menu.lst
Note: I have not yet XP installed. I was just wondering what I had to do after it have been installed - safety precaution, rather then asking help when the computer doesn't boot anymore, after which no internet connection = no help.
DOS boots fine. Linux boots fine too. There still space for a new extended partition. PS: is it possible to enlarge an extended partition? I.e. does something depend on the table and if the talbe would change, that other thing would get broken or confused?
The fdisk output:
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009dfe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63       30239       15088+   4  FAT16 <32M
/dev/sda2           30240    21515759    10742760    5  Extended
/dev/sda5           30303    19565279     9767488+  83  Linux
/dev/sda6        19565343    21515759      975208+  82  Linux swap / Solaris
```

Most comments cut out of the following menu.lst for easier reading. 
```
# menu.lst 
default         0
timeout         10

# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
## DO NOT UNCOMMENT THEM, Just edit them to your needs
## ## Start Default Options ##
## default kernel options for automagic boot options
# kopt=root=UUID=4cb72186-2c06-4fab-957e-e8772f34bf9c ro
# crashdump=0
# groot=(hd0,4)
# alternative=true
# lockalternative=false
# defoptions=quiet splash
# lockold=false
# xenhopt=
# xenkopt=console=tty0
# altoptions=(recovery mode) single
# howmany=all
# memtest86=true
# updatedefaultentry=false
# savedefault=false
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=4cb72186-2c06-4fab-957e-e8772f34bf9c ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=4cb72186-2c06-4fab-957e-e8772f34bf9c ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           FreeDOS
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by Pumalite on 2008-07-03
Post a Gparted screenshot showing the offending partitions.

---

