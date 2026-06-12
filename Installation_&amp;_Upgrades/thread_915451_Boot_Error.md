---
title: "Boot Error?"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by Darth Geek on 2008-09-09
I've just successfully installed Hardy Heron on a spare USB HDD that was lying around.  I installed the 32-bit edition, and made sure to add a boot section in /dev/sdb1.  I'm able to boot from the HDD, but when Grub asks what I want to boot from, selecting Ubuntu 8.04.1 yields an "error 17," which brings me back to grub.  selecting "Windows XP Professional" also loops back to Grub as well.

In case anybody was wondering, the HDD is a 60GB 2.5" EIDE disk that I pulled out of an old laptop and threw into an enclosure.  I'm trying to boot from an Acer Aspire 5520-5334:

Dual core Athlon 64
1GB PC-5300 RAM
nVidia GeForce 7000m, integrated into MB


What is "Error 17" and what Can I do to fix it?

---

### Post by Catalyst2Death on 2008-09-09
Can you boot normally to windows without the usb plugged in?

Check here:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

Hopefully it will get resolved...  I suspect it has to with your bios settings.

---

### Post by caljohnsmith on 2008-09-09
> **Darth Geek said:**
> I've just successfully installed Hardy Heron on a spare USB HDD that was lying around.  I installed the 32-bit edition, and made sure to add a boot section in /dev/sdb1.  I'm able to boot from the HDD, but when Grub asks what I want to boot from, selecting Ubuntu 8.04.1 yields an "error 17," which brings me back to grub.  selecting "Windows XP Professional" also loops back to Grub as well.

In case anybody was wondering, the HDD is a 60GB 2.5" EIDE disk that I pulled out of an old laptop and threw into an enclosure.  I'm trying to boot from an Acer Aspire 5520-5334:

Dual core Athlon 64
1GB PC-5300 RAM
nVidia GeForce 7000m, integrated into MB


What is "Error 17" and what Can I do to fix it?
From the Grub manual:
> Error 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized
Most likely your problem can be solved by simply correcting the OS entries in Grub's /boot/grub/menu.lst. Boot up your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sdb2 or similar) by noticing which partition is "linux" under the "system" category, and then use that:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
And post the results. That will give us a place to start.

---

### Post by Darth Geek on 2008-09-09
sudo fdisk -lu gets us:

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x73e35f85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x449e561e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   112679909    56339923+  83  Linux
/dev/sdb2       112679910   117210239     2265165    5  Extended
/dev/sdb5       112679973   117210239     2265133+  82  Linux swap / Solaris


I'm assuming the second command merely shows menu.lst in the terminal, so here's what that has:

> 
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=67c7e040-c240-4263-981b-599853b6ef21 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=67c7e040-c240-4263-981b-599853b6ef21 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=67c7e040-c240-4263-981b-599853b6ef21 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1



I should also note that I'm posting this from WinXP on my main HDD.  If anyone has links to setting up WiFi and/or listings of compatible network cards, that would be splendid.

---

### Post by caljohnsmith on 2008-09-10
If you are truly booting off your internal HDD sda, then your menu.lst should be correct. I suspect you must be booting off your USB drive though. Before you change anything, next time on start up, select the first Ubuntu entry in the Grub menu, hit "e" to edit it, select the line that says "root (hd1,0)", press "e" to edit it, change it to "root (hd0,0)", press return, then press "b" to boot. If that works, it means you are booting from your USB drive. If that is the case, you can change your Grub's menu.lst so you can boot Ubuntu/Windows. Let me know what happens and we can take it from there.

---

### Post by Darth Geek on 2008-09-10
Okay, that worked out well.  I've booted Ubuntu and am now back in Windows without a hitch.  Thanks for your help! ^_^

---

