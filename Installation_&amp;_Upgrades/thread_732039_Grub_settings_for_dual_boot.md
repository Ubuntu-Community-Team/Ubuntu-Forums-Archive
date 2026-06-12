---
title: "Grub settings for dual boot"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by Optomisticsi on 2008-03-22
Hi guys, I'm new to Linux and have just installed Hardy Heron. Only been using it for an hour or so, but I'm liking what I see! But I have another HDD on my system where I have Vista installed, so I want to dual boot. Looking through these forums I have got as far as looking at the menu.lst in Grub, which is as follows;

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

What I want ideally is for Vista to be my primary OS, and when the system starts up I get a list of OS's, it either starts Vista by default after a delay, or just gives me the option where I must confirm what I want to do. I know I may need to edit something in the menu.lst file, but I have no idea what.

Help anyone?

---

### Post by Kiri on 2008-03-22
Do you know which number partition your vista is installed on? You need to know the disk (probably hd0) and partition number before you can edit the file.
If its the 1st partition on 1st disk it will be hd0,0

Type this into the terminal and post the results here so we can see your disk setup

```
sudo fdisk -l
```

---

### Post by Optomisticsi on 2008-03-22
Ok, Vista is installed on my master HDD (Motherboard Sata 1) and using the only partition on that drive.

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9a06ec3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54f16597

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       34493   277061523+   7  HPFS/NTFS
/dev/sdb2           57763       60801    24410767+  83  Linux
/dev/sdb3           57641       57762      979965   82  Linux swap / Solaris

---

### Post by Kiri on 2008-03-22
Add this at the end of your menu.lst after the ubuntu entries


```
title Microsoft Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1
```


So it will end up like this:

```
## ## End Default Options ##

title Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro quiet splash
initrd /boot/initrd.img-2.6.24-12-generic
quiet

title Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro single
initrd /boot/initrd.img-2.6.24-12-generic

title Ubuntu hardy (development branch), memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet

title Microsoft Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```


Plus all the stuff it already has above that of course

---

### Post by Optomisticsi on 2008-03-22
> **Kiri said:**
> Add this at the end of your menu.lst after the ubuntu entries


```
title Microsoft Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1
```

It's actually Vista I'm running, your solution says XP, does it matter?

---

### Post by Kiri on 2008-03-22
No you can actually change the title line to say anything you want :)

Change it to say Vista, or something else if you want ;)

---

### Post by Shazaam on 2008-03-22
Add this........
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
after this.......
```
## END DEBIAN AUTOMAGIC KERNELS LIST
```
P.S
To change default boot (Vista or Ubuntu, you choose) change this....
```
default 0
```
to whatever you want by counting the kernel entries in menu.lst

---

### Post by Optomisticsi on 2008-03-22
> **Kiri said:**
> No you can actually change the title line to say anything you want :)

Change it to say Vista, or something else if you want ;)

I've tried what you said, but once I've pasted in the changes, it won't let me save it, saying;

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Is this Ubuntu's version of Vista's User Account Control?

---

### Post by Kiri on 2008-03-22
You need to be root.

type this form the terminal:

```

sudo gedit menu.lst

```

making sure you are in the same dir as menu.lst
Then you should be able to save

---

### Post by Shazaam on 2008-03-22
No. You need to edit menu.lst as root. Do this in terminal.....
```
gksudo gedit /boot/grub/menu.lst
```
(small L)
enter your user password (don't worry, it's there) and hit enter. Make a backup copy of menu.lst first. When you are done editing save it. (File>Save)

---

### Post by Optomisticsi on 2008-03-22
Ok, this is what I have, but nothing's changed;

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

title 		Microsoft Windows Vista
root 		98oi(hd0,0)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Grub still doesn't give me Vista as an option, just Linux. I think we're getting close though.

---

### Post by Kiri on 2008-03-22
> ### END DEBIAN AUTOMAGIC KERNELS LIST

this should be the absolute LAST line in the file

---

### Post by Shazaam on 2008-03-22
> **Kiri said:**
> this should be the absolute LAST line in the file
Really? Mine works perfectly.
```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=59bb43d3-f1c8-4f58-95e0-f1bca70f34a4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=59bb43d3-f1c8-4f58-95e0-f1bca70f34a4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		PuppyLinux (on /dev/sda6)
root		(hd1,5)
kernel		/boot/vmlinuz root=/dev/sda6 
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
#title		MEPIS (on /dev/sda7)
#root		(hd1,6)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda7 nomce quiet vga=791 
#savedefault
#boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu Dapper(on /dev/sda8)
root		(hd1,7)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda8 ro quiet splash
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu Dapper, (recovery mode) (on /dev/sda8)
root		(hd1,7)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/sda8 ro single
savedefault
boot
```
My fstab.....
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=59bb43d3-f1c8-4f58-95e0-f1bca70f34a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=4A20682920681DE7 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=8b9e033a-da8b-419d-9f61-afe834a42d9e /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=d0784552-b31a-446f-96b7-3cf74df20207 /media/sda7     ext3    defaults        0       2
# /dev/sda8
UUID=d75f750c-61d3-4d38-b172-cd5a2c27500f /media/sda8     ext3    defaults        0       2
# /dev/sda5
UUID=6cb2b284-2f2d-43d5-bb51-6c0813d94809 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```
fdisk -l........
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38626   310263313   5  Extended
/dev/sda5               1         781     6273319  82  Linux swap / Solaris
/dev/sda6             782        3350    20635461   83  Linux
/dev/sda7            3351        8471    41134401   83  Linux
/dev/sda8            8472       26554   145251666   83  Linux
/dev/sda9   *       26555       38626    96968308  83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000096f6

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

```

---

### Post by Kiri on 2008-03-22
Oh really? Then I guess it doesnt matter :)

In that case I dont know what the problem is though...

---

### Post by Kiri on 2008-03-22
Oh! you have 2 entries for vista! get rid of the first one.

it should look like this:

> 


title Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro quiet splash
initrd /boot/initrd.img-2.6.24-12-generic
quiet

title Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=d2cb7111-985f-46b7-aecc-87a3a211884a ro single
initrd /boot/initrd.img-2.6.24-12-generic

title Ubuntu hardy (development branch), memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1


---

### Post by wRonG1 on 2008-03-22
> **Kiri said:**
> Oh! you have 2 entries for vista! get rid of the first one.

it should look like this:


Kiri : Your suggestions certainly helped _me_ out !  I could not over weeks , sort out why I seemed to be able to install Ubuntu to a separate drive , but not _boot_  in a dual-boot situation . Your simple boot edit fixed me up - but not before I figured out how to boot by switching my BIOS boot order ; how to get into root to edit , then switch back BIOS to test !    
Question : I've seen suggestions that
 
title Microsoft Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1  

--- should be entered _before_ ### END DEBIAN AUTOMAGIC KERNELS LIST in order to prevent it's alteration after an upgrade . 
Comments ? I realize new Ubuntu is imminent .

---

### Post by Kiri on 2008-03-23
> 
Question : I've seen suggestions that
 
title Microsoft Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1  

--- should be entered _before_ ### END DEBIAN AUTOMAGIC KERNELS LIST in order to prevent it's alteration after an upgrade . 
Comments ? I realize new Ubuntu is imminent .


Well, glad I helped someone at least ;)

About your question. I'm not really sure, but I think that line should generally be last in the file, so if something tries to update the file it might look for that line and not add things after it...?
Sorry, I'm not really sure, but I would just put it last since I think that is the format it is meant to be. And of course you had better copy the file somewhere before you upgrade so you can always refer to your original file if it gets overwritten. If you do that, I think you will have no problem. The menu.lst files seem relatively simple, so most things should be fixable if it is only a problem in that. 
Good luck!

---

### Post by Optomisticsi on 2008-03-23
Ok, well it's finally working thanks to your help guys. Also found a great website that gives SUPERB directions for setting up dual boot in various scenarios. Explains it in foolproof terms too!!

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

I hope this helps anyone else that needs it!

---

