---
title: "Triple boot with Ubuntu, Debian and Windows XP"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Ellimist on 2010-05-18
I had a dual booting system with Xubuntu Lucid and Windows XP. Today, while installing Debian Lenny, I mistakenly overwrote Grub2 with the Grub legacy that came with Debian.

I tried editing menu.lst and adding an entry for Ubuntu, but booting to Ubuntu fails with the error :
"Filesystem type unknown, partition type 0x82.
Error 17 :Cannot mount selected partition."

Xubuntu resides on an Ext4 partition.

Grub's menu.lst looks like this :
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hdb10 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,9)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.26-2-686
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/hdb10 ro 
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/hdb10 ro single
initrd		/boot/initrd.img-2.6.26-2-686 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Ubuntu, with Linux 2.6.32-22-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=4cf0fedf-c2db-4d5d-9c21-4c8471e162b8 ro   quiet splash elevator=deadline
initrd		/boot/initrd.img-2.6.32-22-generic


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Unfortunately, my optical drive doesn't work anymore, so I don't have the option of booting using a Live CD.

---

### Post by oldfred on 2010-05-18
Not all versions of grub legacy are updated to use ext4 partitions. Ubuntu updated their copy but grub 0.97 has had no central updates for years. Each distribution may make minor changes even though it still is 0.97.

I would just reinstall grub2. Follow the directions for installing from a Cd but boot into debian and chroot into ubuntu. It will install grub2 from the chroot. I do not know if the simple version will work if debian is using old grub.

Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by Ellimist on 2010-05-18
I think I understand what you are saying about chrooting into Ubuntu. I'll try it and post here with the results and problems (if any).

---

### Post by Ellimist on 2010-05-18
Unfortunately, Debian cannot apparently mount ext4 partitions.

mount -t ext4 /dev/sda8 /mnt gives "mount: unknown filesystem type 'ext4'",

---

### Post by oldfred on 2010-05-18
How did you install. Can you boot from a USB? Then you can use that as a liveCD.

---

### Post by Ellimist on 2010-05-18
Was able to mount the drive. Used the solution in this thread : [http://forums.debian.net/viewtopic.php?t=33401](http://forums.debian.net/viewtopic.php?t=33401)

I'll post if the chrooting and the grub update succeeded.

---

### Post by Ellimist on 2010-05-18
Thankies! It worked!

I booted into Ubuntu and did an update-grub. It said :

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Debian GNU/Linux (5.0.4) on /dev/sda10
done

Yay!

Thanks for sticking with me, oldfred.:)

---

### Post by oldfred on 2010-05-18
Glad you got it working, not sure the difference in the way you mount though. But as long as it works that is what counts.

---

