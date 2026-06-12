---
title: "Crashed again"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by gos1 on 2008-03-08
Hi :
 
I tried to use Ubuntu several times and I had the same problem and returned to Windows again and again . I upgraded the Kubuntu and it crashed again . I have to solve this problem If i will use Ubuntu . How can I restore all the upgrades and make the system like it was . The error it is giving now is file not found press any key to continue and I can do nothing about that . Please someone help me / I want to use this system but it is killing me to be able to do nothing when everything crashes. As I said only thing I have done was to run the update manager .

---

### Post by Pumalite on 2008-03-08
Give us more details. Can you boot to it now? What are the exact error messages?

---

### Post by gos1 on 2008-03-08
No I cannot boot now . I am using the live cd . And the only error I get is 

Grub loading ==>
 
 Error 15: File not found 
 press any key to continue 

 When I press a key it returns to grub and gives the same error when I choose an OS

---

### Post by Pumalite on 2008-03-08
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
Post from the Terminal:
sudo fdisk -lu

---

### Post by gos1 on 2008-03-08
<code>
sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x166d166d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   154063349    77031643+  83  Linux
/dev/sda2       154063350   156296384     1116517+   5  Extended
/dev/sda5       154063413   156296384     1116486   82  Linux swap / Solaris
</code>


This is the answer I get

---

### Post by Pumalite on 2008-03-08
Mount your partition:
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
Now post the output of:
cat /media/sda1/boot/grub/menu.lst

---

### Post by gos1 on 2008-03-08
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
# kopt=root=UUID=9194343c-c456-4b87-b375-db38b1dda1bf ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9194343c-c456-4b87-b375-db38b1dda1bf ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9194343c-c456-4b87-b375-db38b1dda1bf ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by gos1 on 2008-03-08
i cannot boot the computer after installing the updates . Can the Kernel version be different . If so how can I understand that ...

---

### Post by gos1 on 2008-03-09
I checked the kernel version and it fits the menu.lst ...

---

### Post by Pumalite on 2008-03-09
Try reconfiguring your xserver:
Ctrl+Alt+F1 to get a command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by gos1 on 2008-03-09
i am using kubuntu can I do that from the live cd because I cannot open the actual drive

---

### Post by Pumalite on 2008-03-09
What happens when you boot? (not the Live CD)

---

