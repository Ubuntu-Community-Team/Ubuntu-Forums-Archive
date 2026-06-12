---
title: "Grub Option Adding???"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by Ciggy on 2008-03-31
I installed Kubunto onto another Hard Drive. I restarted my system but Kubuntu is not in the Grub I know how to edit the Grub setting but how do I add Kubuntu?

edit: On my first drive I have Vista and Ubuntu installed so I can edit my Grub using Ubuntu Terminal.

---

### Post by zvacet on 2008-03-31
You can try [this #2](http://ubuntuforums.org/showthread.php?t=740664)

---

### Post by Ciggy on 2008-03-31
Kubuntu is on my slaved drive... the drive doesnt have a name so what would the path be?

---

### Post by logos34 on 2008-03-31
> **Ciggy said:**
> Kubuntu is on my slaved drive... the drive doesnt have a name so what would the path be?

**(hd1,0)**, if kubuntu root is the first partition of second drive.  You might want to use [configfile or symlink]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") entry format

> title        Kubuntu Gutsy Gibbbon 7.10
configfile   (hd1,0)/boot/grub/menu.lst

---

### Post by Ciggy on 2008-03-31
I got disc read erorr trying to access Kubuntu like this.

[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		85

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color white/black blink-red/black

#A splash image for the menu
#splashimage=(hd0,2)/boot/grub/splashimages/appleblack.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=984e0137-a0b7-47cb-b083-8809d51d7e69 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=quiet splash vga=792

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

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Linux:
root


title		Ubuntu 7.10
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=984e0137-a0b7-47cb-b083-8809d51d7e69 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=984e0137-a0b7-47cb-b083-8809d51d7e69 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Windows:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1



title Kubuntu Gutsy Gibbbon 7.10
configfile (hd1,0)/boot/grub/menu.lst
[/PHP]

---

### Post by zvacet on 2008-03-31
Maybe [this](http://ubuntuforums.org/showthread.php?t=724817&highlight=boot) can help you.

---

### Post by Ciggy on 2008-03-31
output of sudo sdisk -1
```
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

When I installed Kubunto I did not install Grub on it because after the install I restarted the PC and now I can not get on Kubuntu

---

### Post by bodhi.zazen on 2008-03-31
can you post the output of :

```
sudo fdisk -l
```

That is a small "L" and not the number 1

---

### Post by Ciggy on 2008-03-31
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13928   111875529    7  HPFS/NTFS
/dev/sda2           18706       19458     6041464    7  HPFS/NTFS
/dev/sda3           13929       18503    36748687+  83  Linux
/dev/sda4           18504       18705     1622565    5  Extended
/dev/sda5           18504       18705     1622533+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae706b65

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14334   115137823+  83  Linux
/dev/hdb2           14335       14946     4915890    5  Extended
/dev/hdb5           14335       14946     4915858+  82  Linux swap / Solaris
```

---

### Post by bodhi.zazen on 2008-03-31
OK, in Ubuntu, 

```
gksu gedit /boot/grub/menu.lst
```

Add this:

> title Kubuntu
root (hd1,0)
chainloader +1
boot

Now boot the live CD

```
sudo grub
```

At the grub prompt :

```
root (hd1,0)
setup (hd1,0)
quit
```

Reboot, all should be well, you will get two grub screens, but that is OK.

FYI You can install KDE on Ubuntu (sudo apt-get install kubuntu-desktop).

---

### Post by Ciggy on 2008-03-31
```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd1,0)

grub> setup (hd1,0)

Error 17: Cannot mount selected partition

grub> quit

```

is what I get.

---

### Post by bodhi.zazen on 2008-03-31
I believe this is an issue with your BIOS, 

Try this link : [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Ciggy on 2008-03-31
Thanks for your help. I ran the install for the KDE in ubuntu like you mentioned and nothing changed could you point me to a tuturial on how to manage that?

---

### Post by confused57 on 2008-03-31
> **Ciggy said:**
> Thanks for your help. I ran the install for the KDE in ubuntu like you mentioned and nothing changed could you point me to a tuturial on how to manage that?
Have you checked in your bios setup to see if your hdb IDE controller is set to "Auto"?

To install Kubuntu alongside Ubuntu, open a terminal in Ubuntu then issue the command bodhi.zazen gave you:
```
sudo aptitude install kubuntu-desktop
```

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

