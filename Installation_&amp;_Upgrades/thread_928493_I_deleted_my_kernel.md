---
title: "I deleted my kernel"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by mavuashire on 2008-09-24
Yesteday while trying to get right kernel because the one i was using aparently had Xen support which does not work with nvidia, I ended up deleting my kernel. Yeah, it's stupid but that is what I did. "sudo apt-get remove 'uname -r" or something like it.

the thing is I had deleted some which were showing to be for 64 bit using the synapic manager and asked me if I wanted to keep the menu.lst and I answered yes. But running it from the shell was distrous. 

Question: can I reinstall the kernel using live cd? Please I have valuable data in here. University thesis. So I need to get that infor atleast.

---

### Post by Sealbhach on 2008-09-24
You can probably retrieve your data using the Live CD. I would rescue all that stuff first, stick it on a USB drive.
-----------------------------------

Then look at fixing your system.

What happens when you try to boot into Ubuntu?


.

---

### Post by mavuashire on 2008-09-24
When I try to boot into ubuntu it says 

Error 15: Unable to open file 
Press any key to continue...

---

### Post by sisco311 on 2008-09-24
> **mavuashire said:**
> Yesteday while trying to get right kernel because the one i was using aparently had Xen support which does not work with nvidia, I ended up deleting my kernel. Yeah, it's stupid but that is what I did. "sudo apt-get remove 'uname -r" or something like it.

the thing is I had deleted some which were showing to be for 64 bit using the synapic manager and asked me if I wanted to keep the menu.lst and I answered yes. But running it from the shell was distrous. 

Question: can I reinstall the kernel using live cd? Please I have valuable data in here. University thesis. So I need to get that infor atleast.

yes. boot with the live cd, mount the root partition and run the commands:
```
sudo chroot /media/mount-point
sudo aptitude install linux-image-generic
```to install the latest generic kernel.
 
assuming that the root ("/") partition is mounted in /media/mount-point

---

### Post by mavuashire on 2008-09-24
it says my mount-point (/media/sda2) is not a file or directory

---

### Post by sisco311 on 2008-09-24
How did you mount the partition?

```
sudo mkdir /media/sda2
sudo mount -t ext3 -o defaults /dev/sda2 /media/sda2
```

---

### Post by mavuashire on 2008-09-24
I did something semilar to that but now when I try to install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image is a virtual package provided by:
  linux-image-2.6.17-10-server-bigiron 2.6.17-10.33
  linux-image-2.6.17-10-server 2.6.17-10.33
  linux-image-2.6.17-10-generic 2.6.17-10.33
  linux-image-2.6.17-10-386 2.6.17-10.33
You should explicitly select one to install.
E: Package linux-image has no installation candidate


sudo apt-get install linux-image-2.6.17-10-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Sealbhach on 2008-09-24
Hi please follow the steps in this thread here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and let us know the result.

It's only a few simple steps.


.

---

### Post by mavuashire on 2008-09-24
I have tried those commands before and after your recommendation trying to find what I could have missed. But I was without luck. They work fine and say there was success in installing grub but I still cannot boot into my ubuntu.

---

### Post by sisco311 on 2008-09-24
boot with the live cd, mount the partition and post:
```
ls -l /media/*mount-point*/boot
```
and
```
cat /media/*mount-point*/boot/grub/menu.lst
```

---

### Post by mavuashire on 2008-09-24
Here are the results of directory list and menu.lst

ubuntu@ubuntu:/mnt/sda2$ ls -l /mnt/sda2/boot
total 112
drwxr-xr-x 2 root root   4096 2008-09-25 00:01 grub
-rw-r--r-- 1 root root 103204 2007-09-28 10:06 memtest86+.bin
ubuntu@ubuntu:/mnt/sda2$ cat /mnt/sda2/boot/grub/menu/lst
cat: /mnt/sda2/boot/grub/menu/lst: No such file or directory
ubuntu@ubuntu:/mnt/sda2$ cat /mnt/sda2/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu 8.04, kernel 2.6.24-19-server
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-server root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-server
quiet

title           Ubuntu 8.04, kernel 2.6.24-19-server (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-server root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2 ro single
initrd          /boot/initrd.img-2.6.24-19-server

title           Ubuntu 8.04, kernel 2.6.24-19-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title          Microsoft Windows XP Professional
#root           (hd0,0)
#savedefault
#makeactive
#chainloader    +1

ubuntu@ubuntu:/mnt/sda2$

---

### Post by sisco311 on 2008-09-24
also post:
```
ls -l /boot
```

---

### Post by mavuashire on 2008-09-24
> **sisco311 said:**
> also post:
```
ls -l /boot
```

It is there at the top

---

### Post by sisco311 on 2008-09-24
copy the kernel from the live cd to the disk:
```
sudo cp /boot/vmlinuz-2.6.24-16-generic /media/sda2/boot
sudo cp /boot/initrd.img-2.6.24-16-generic /media/sda2/boot

```

add a new entry to the menu.lst:

edit the file
```
gksu gedit /media/sda2/boot/grub/menu.lst
```and add:
> 

...

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2 ro single
initrd /boot/initrd.img-2.6.24-16-generic

[B]title Ubuntu LIVE CD KERNEL
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2437972c-f21d-4dad-ad71-97d98d9196c2
initrd /boot/initrd.img-2.6.24-16-generic[/B]

title Ubuntu 8.04, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title Microsoft Windows XP Professional
#root (hd0,0)
#savedefault
#makeactive
#chainloader +1



save the file and reboot.
select **Ubuntu LIVE CD KERNEL** from the grub menu.

---

### Post by mavuashire on 2008-09-24
I think I listed the wrong directory last time

ls -l boot on the live cd default directory is here

As can be seen, there is no "initrd.img-2.6.24-16-generic"

> 
-rw-r--r-- 1 root root  285604 2006-10-13 19:09 abi-2.6.17-10-generic
-rw-r--r-- 1 root root   74645 2006-10-13 16:13 config-2.6.17-10-generic
drwxr-xr-x 2 root root      80 2008-09-24 23:56 grub
-rw-r--r-- 1 root root   94600 2006-10-20 11:44 memtest86+.bin
-rw-r--r-- 1 root root  728690 2006-10-13 19:09 System.map-2.6.17-10-generic
-rw-r--r-- 1 root root 1636681 2006-10-13 19:09 vmlinuz-2.6.17-10-generic



> root@ubuntu:/# ls -l
total 5
drwxr-xr-x   2 root root   520 2008-09-25 00:08 bin
drwxr-xr-x   3 root root    60 2008-09-24 23:56 boot
dr-xr-xr-x  14 root root  4096 2006-10-25 14:35 cdrom
drwxr-xr-x  12 root root 13620 2008-09-24 23:35 dev
drwxr-xr-x 116 root root  1920 2008-09-24 23:48 etc
drwxr-xr-x   3 root root    60 2008-09-25 09:34 home
drwxr-xr-x   2 root root     3 2006-10-25 13:26 initrd
lrwxrwxrwx   1 root root    33 2006-10-25 13:34 initrd.img -> boot/initrd.img-2.6.17-10-generic
drwxr-xr-x  20 root root   100 2008-09-25 00:08 lib
drwxr-xr-x   2 root root     3 2006-10-25 13:26 media
drwxr-xr-x   3 root root    60 2008-09-24 23:47 mnt
drwxr-xr-x   2 root root     3 2006-10-25 13:26 opt
dr-xr-xr-x 123 root root     0 2008-09-25 09:33 proc
drwxr-xr-x  20 root root   256 2006-10-25 13:34 rofs
drwxr-xr-x   7 root root   220 2008-09-25 00:10 root
drwxr-xr-x   2 root root   220 2008-09-25 00:08 sbin
drwxr-xr-x   2 root root     3 2006-10-25 13:26 srv
drwxr-xr-x  11 root root     0 2008-09-25 09:33 sys
drwxrwxrwt  12 root root   300 2008-09-24 23:56 tmp
drwxr-xr-x  14 root root   100 2008-09-25 00:08 usr
drwxr-xr-x  20 root root   140 2008-09-24 23:35 var
lrwxrwxrwx   1 root root    30 2006-10-25 13:34 vmlinuz -> boot/vmlinuz-2.6.17-10-generic


---

### Post by Sealbhach on 2008-09-25
Q. Did you retrieve your data?

If so, it might be more straightforward to just reinstall.


.

---

