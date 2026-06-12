---
title: "Can no longer boot into Windows from GRUB. Please help!"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by timryan on 2008-05-06
Just last night I installed Ubuntu 8.04 on a 300GB external USB hard drive. I have Windows Vista on my internal hard drive. Ubuntu was working perfectly last night, and still is. However today, when I tried to boot into Windows Vista from GRUB, I select the "Windows Vista/Longhorn (loader)" option and it gives me this error: "Error 29: Disk write error. Press any key to coninue..." and it just goes back to the GRUB loader.

So, I tried disconnecting my USB hard drive and booting up to see if it would automatically boot into windows but when I do GRUB doesn't load, it just says "Error 21" and nothing happens. 

I've tried fiddling around with the boot order, making sure my internal hard drive is the priority but nothing seems to work. Please help.

---

### Post by Pumalite on 2008-05-06
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)
[http://users.bigpond.net.au/hermanzone/p15.htm#29](http://users.bigpond.net.au/hermanzone/p15.htm#29)
Post:
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by timryan on 2008-05-06
For some great reason my computer has decided to stop detecting my external HD, so as soon as I fix this new problem, I'll post the contents of both those commands.

---

### Post by Pumalite on 2008-05-06
Replace cables if necessary. Check your connections.

---

### Post by timryan on 2008-05-06
I've replaced my USB cable that connects my HD with two separate ones and have tried connecting it to my laptop to see if my laptop recognizes it and it doesn't. So, I guess my HD has decided to fail on me. I have a feeling its not the HD itself and its probably the USB connector (its somewhat wobbly). So, now I am unable to get into either OS. Is there anyway I can remove GRUB or do something to get back into Vista? I really appreciate the help. Thanks. 

****EDIT****

My HD has now decided to cooperate and I will post the results of the two commands you mentioned earlier.

---

### Post by xzero1 on 2008-05-06
Part of grub is probably on your Ubuntu (external drive) so grub does not know about Vista. You should be able to boot with a super grub disk. Never tried it with Vista though.

---

### Post by Pumalite on 2008-05-06
Super Grub will fix the MBR in your Vista:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by timryan on 2008-05-06
The results of sudo fdisk -l:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2de19bf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37439   300728736   83  Linux
/dev/sdb2           37440       38913    11839905    5  Extended
/dev/sdb5           37440       38913    11839873+  82  Linux swap / Solaris

```

And the results of cat boot/grub/menu.lst:

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
# kopt=root=UUID=3dbc6799-07e7-4fb7-b0c7-3fd5d258ba0d ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3dbc6799-07e7-4fb7-b0c7-3fd5d258ba0d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3dbc6799-07e7-4fb7-b0c7-3fd5d258ba0d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by timryan on 2008-05-06
Alright, I'll look into super grub right now. Thanks so much for the help!

---

### Post by Pumalite on 2008-05-06
Your fdisk and your menu.lst are in concordance.

---

### Post by timryan on 2008-05-06
Alright, one last question. I am now in Windows, SuperGRUB allowed me to get here. How do I go about fixing the MBR for Vista? I'm extremely apprehensive about what options to select, I just don't want to screw anything up. Theres an option to fix Windows boot record, and when I go into it there isnt an option for Vista, only Win XP, 2003, 98, etc... Again, thanks for all the help!

---

### Post by knitmom on 2008-05-08
I'm having the same problem now too!  Sorry to bother you again.  I can load Ubuntu, but vista won't load.  Here are my results from the sudo fdisk -l and cat /boot/grub/menu.lst commands.
> lynn@lynn-desktop:~$ sudo fdisk -l
[sudo] password for lynn: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7008d0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000    7  HPFS/NTFS
/dev/sda2   *        1275        6374    40958131    7  HPFS/NTFS
/dev/sda3            6375        9729    26949037+   5  Extended
/dev/sda5            6375        6617     1951866   82  Linux swap / Solaris
/dev/sda6            6618        9049    19535008+  83  Linux
/dev/sda7            9050        9729     5462068+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc349d8d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+   c  W95 FAT32 (LBA)
/dev/sdb2            1217        9730    68381696    7  HPFS/NTFS

lynn@lynn-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=d50b054e-5516-4ff3-aed2-0b7a22a8540a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d50b054e-5516-4ff3-aed2-0b7a22a8540a ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d50b054e-5516-4ff3-aed2-0b7a22a8540a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

lynn@lynn-desktop:~$ 



Should the vista loader be at (hd0,2) since that is where my windows is loaded?  According to the fdisk windows is at /dev/sda2   I'm not sure what is on sda1, it might be preloaded software on the hard drive from the manufacturer.

Thanks,
Knitmom

---

### Post by Pumalite on 2008-05-08
Change the 'root' of the Vista entry to (hd0,1)

---

