---
title: "Grub error 22:  Partition not found"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by xRaVagEx on 2008-03-02
Hi all,
Ran into a bit of a road bump installing Gutsy last night.
I have 3 SATA drives on my rig.  I partiioned my spare 500gig in 1/2 and put ubuntu on it.  Since then, I have not been able to get ubuntu to load up.  

I used Super Grub to fix the Error 17 I was getting originally.  Now when Grub loads, I'm able to select XP and it loads up fine, but when I pick Ubuntu 7.10, I'm getting Error 22: Partition not found.  My best guess is that grub is not loading the proper partition, and I'm at a bit of a loss of how to get it to recognize the proper one to boot.  

Can anyone point me in the right direction?  :)

Here's my fdisk info:  
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe166e166

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   420340724   210170331    7  HPFS/NTFS
/dev/sda2       420340725   625137344   102398310    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf7e86f4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   524956004   262477971    7  HPFS/NTFS
/dev/sdb2       524956005   964606859   219825427+  83  Linux
/dev/sdb3       964606860   976768064     6080602+   5  Extended
/dev/sdb5       964606923   976768064     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa561a561

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   156280319    78140128+   7  HPFS/NTFS

menu.lst:
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
# kopt=root=UUID=8414c8b7-7080-4554-87db-57e06df96312 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8414c8b7-7080-4554-87db-57e06df96312 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8414c8b7-7080-4554-87db-57e06df96312 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
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
makeactive
chainloader	+1

---

### Post by louieb on 2008-03-02
Looks to me that the fdisk output and your menu.lst file match up. Ubuntu is on the 2nd drive in the 2nd partition.
One more place to check. Please post
/boot/grub/device.map
Maybe the answer is there.

---

### Post by xRaVagEx on 2008-03-02
Here's the device.map

> (hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

---

### Post by louieb on 2008-03-02
Nothing odd there either.
Lets get grub to find itself.
when the grub menu comes up press **c** to get the command line prompt **grub> **and enter
```
find /boot/grub/stage1
```should return (hd1,1) but we already know that doesn't work. 
So it will be interesting to see what it returns.
Anyway after it returns something press esc to return to the grub menu and highlight the Ubuntu entry and press **e** to edit and then edit the root line and change it to whatever (hd#,#) you got from your command line find.

---

### Post by xRaVagEx on 2008-03-02
The return I got was (hd2,1)

When I went to edit the root line, it had (hd1,1).  When I try to change it to (hd2,1), it reboots  goes back to (hd1,1).
after reboot, its back the way it was, grub at (hd2,1) and root at (hd1,1)


Thanks for helping btw louieb  :)

---

### Post by louieb on 2008-03-02
ok now to make it permanent. edit /boot/grub/menu.lst.

Press Alt+F2 to bring up a run dialog or in a terminal window.
```

gksudo gedit /boot/grub/menu.lst
```

Not real clear did (hd2,1) work?

---

### Post by xRaVagEx on 2008-03-02
[QUOTE=louieb;4441861]ok now to make it permanent. edit /boot/grub/menu.lst.

Press Alt+F2 to bring up a run dialog or in a terminal window.
```

gksudo gedit /boot/grub/menu.lst
```

(hd2,1) worked like a charm.  I just noobed it up the first 2 times by forgetting to hit 'b'.

Thank you so much louieb!!  Now to ween myself off windows and re-familiarize myself with Linux.  

Thanks again,
Chris

---

### Post by jokerinux on 2008-04-29
hi,

i have the same damn errore (22)

i post here also my informations, i hope this will be helpful

thanks

fdisk -l
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b5b7b58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19929   160079661    7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0544287c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6faa6faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3855    30965256    7  HPFS/NTFS
/dev/sdc2            3856       10308    51833722+   f  W95 Ext'd (LBA)
/dev/sdc3           10309       38913   229769662+   7  HPFS/NTFS
/dev/sdc5            3856        5209    10875973+  83  Linux
/dev/sdc6            5210        5340     1052226   82  Linux swap / Solaris
/dev/sdc7            5341       10308    39905428+  83  Linux


```

menu.lst
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
# kopt=root=UUID=d24f23db-95df-409b-8c0d-11d69fa9bb6d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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
# defoptions=quiet splash xforcevesa

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d24f23db-95df-409b-8c0d-11d69fa9bb6d ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d24f23db-95df-409b-8c0d-11d69fa9bb6d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


```

device.map

```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

---

### Post by Trututu on 2008-04-29
My XP doesn't boot either, check out:
fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2d6c2d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5124    41158498+   7  HPFS/NTFS
/dev/sda2            5125        6125     8040532+  83  Linux
/dev/sda3            6126        9631    28161945    c  W95 FAT32 (LBA)
/dev/sda4            9632        9729      787185    f  W95 Ext'd (LBA)
/dev/sda5            9632        9729      787153+  82  Linux swap / Solaris

```

menu.lst
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
timeout		5

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
# kopt=root=UUID=24f20bd7-80d4-4b1c-8880-50e4fdfda9b0 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24f20bd7-80d4-4b1c-8880-50e4fdfda9b0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24f20bd7-80d4-4b1c-8880-50e4fdfda9b0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

```

Any ideas? :confused::(

---

### Post by jokerinux on 2008-05-02
can someone help us please?
:(

---

### Post by Wootyeah on 2008-06-08
I had this problem.  My original hard drive was a SATA plugged into slot 6.  When I put in my new hard drive, I just plugged it into slot 5 right below it thinking it wouldn't really make a difference.  I came up with that error 22 thing saying partition not found.  I took it in to have some ppl look at it, and this is what they found:  That the primary/first hard drive needs to be plugged into slot 1.  The later ones plugged in later.  It fixed it.

---

