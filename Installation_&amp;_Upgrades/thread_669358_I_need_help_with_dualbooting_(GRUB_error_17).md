---
title: "I need help with dualbooting (GRUB error 17)"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by 449 on 2008-01-16
I installed Debian to my /sda3. When I tried to restart, I get the Grub error 17. If you guys need any more information just say the word. Thanks for your time. I'm able to boot Ubuntu in super grub, but Debian is not even listen as a choice. 

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23844   191518897+  83  Linux
/dev/sda2           30218       30401     1477980    5  Extended
/dev/sda3           23845       30217    51191122+  83  Linux
/dev/sda5           30218       30401     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

**GRUB menu list**
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
# kopt=root=UUID=7c6c507a-52fb-47cf-93d1-c2ebd6f4518e ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c6c507a-52fb-47cf-93d1-c2ebd6f4518e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c6c507a-52fb-47cf-93d1-c2ebd6f4518e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by wolfen69 on 2008-01-16
try Super Grub disk [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

---

### Post by 449 on 2008-01-16
> **wolfen69 said:**
> try Super Grub disk [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

Last sentence at the top.

---

### Post by 449 on 2008-01-16
Can anyone help me out here? I have no clue what I'm doing.

Thanks.

---

### Post by RockHaxor on 2008-01-16
Here’s the quick and easy way to re-enable Grub.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub “prompt”, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation
```
sudo grub
root (hd0,0)
setup (hd0)
exit
```

Reboot (removing the livecd), and your boot menu should be back.

---

### Post by 449 on 2008-01-16
Hm, I think I did that without even knowing it earlier ,because now I no longer get the error, but I still can't boot off my 2nd partition. When I press Esc when GRUB is loading Ubuntu is the only OS listed. Does that make any sense? :confused:

---

### Post by RockHaxor on 2008-01-16
When installing the second Linux system, a boot loader may have been installed in its root partition. If so, add the following section for the second system to the boot loader configuration file of the first installation  (/boot/grub/menu.lst):

open a terminal: **applications/accessories/terminal: **

insert this code:
```
sudo gedit /boot/grub/menu.lst
```

Copy this code and insert it at the bottom of this open document (you can call the Linux distro whatever you want)

```
title Linux Two
   root (hd0,2)
   chainloader +1
```

This entry (hd0,2) is based on the assumption that the new distro is on the 3rd partition

Save this document and reboot your system.

If the boot loader was also installed in the debian install this should work

Good Luck!

---

### Post by 449 on 2008-01-16
This is strange. I tried using what I have here, and it was able to load grub, however instead of loading up Debian, It loaded up Ubuntu! And I specifically told the Debian installer to install grub to (hd0,2) Any idea what's going on? :confused: 

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c6c507a-52fb-47cf-93d1-c2ebd6f4518e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c6c507a-52fb-47cf-93d1-c2ebd6f4518e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title Debian Etch 4.0
   root (hd0,2)
   chainloader +1



### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by RockHaxor on 2008-01-16
try inserting the command "makeactive" in the code you pasted before. It should then look like this:

```
title Debian Etch 4.0
   root (hd0,2)
   makeactive
   chainloader +1
```

good luck!

---

### Post by 449 on 2008-01-16
Still no luck. 	](*,)

---

### Post by 449 on 2008-01-16
Maybe reinstalling grub would fix this? I'm really lost on this one...

---

### Post by adrian15 on 2008-01-17
> **449 said:**
> I installed Debian to my /sda3. When I tried to restart, I get the Grub error 17. If you guys need any more information just say the word. Thanks for your time. I'm able to boot Ubuntu in super grub, but Debian is not even listen as a choice. 


Are you sure that you installed grub alongside Debian? Maybe you installed Lilo or maybe you did not install any bootloader ?

adrian15

---

### Post by jken146 on 2008-01-17
What I would do is this:

Mount /dev/sda3 somewhere (let's say /mnt/sda3).
```
sudo mount /dev/sda3 /mnt/sda3
```
Find the menu.lst file of debian's GRUB.  Probably:
```
ls /mnt/sda3/boot/grub/
```
Take a look at this file to see what the **kernel** and **initrd** lines are.
```
cat /mnt/sda3/boot/grub/menu.lst | less
```
Copy those lines into the entry for Debian in your Ubuntu menu.lst file, so that it ends up looking like one of your Ubuntu entries.

---

### Post by 449 on 2008-01-17
[[IMG]http://img186.imageshack.us/img186/7858/screenshotdl6.th.png[/IMG]](http://img186.imageshack.us/my.php?image=screenshotdl6.png)

Debian on the left, Ubuntu on the right, still gives me error 17.

---

### Post by 449 on 2008-01-17
I'm using this grub menu and yet I still get error 17 for debian.

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c6c507a-52fb-47cf-93d1-c2ebd6f4518e ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c6c507a-52fb-47cf-93d1-c2ebd6f4518e ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7c6c507a-52fb-47cf-93d1-c2ebd6f4518e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

---

### Post by 449 on 2008-01-17
Could someone explain how I could make a working bootdisk?

---

### Post by adrian15 on 2008-01-18
One reason why Debian does not boot is that your Debian kernel is not installed correctly. You would need to run ```
apt-get install kernel
``` or ```
apt-get install linux
``` from a Debian chroot enviroment.

Another reason why Debian does not boot is because menu.lst is incorrect. You would need to run ```
update-grub
``` inside a Debian chroot environment.

If you could copy-paste here the output of ```
ls -l /mnt/sda3/boot/grub
``` here we might improve the help we give you.

adrian15

---

