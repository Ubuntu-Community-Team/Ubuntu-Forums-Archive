---
title: "Vista boots from SGD but not from Grub"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by eddie_gordo on 2008-05-08
Hi there..

I have just installed Ubuntu 8.04 on my Asus F3Ja laptop... Just before that I installed Vista.. 

When I boot my laptop it shows:

> Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, memtest86+

Windows Vista/Longhorn (loader)
Windows Vista/Longhorn (loader)

But when I choose Windows Vista it doesn't boot, it just reboots again and again and again... I can only access Ubuntu.. I already tried to edit the menu.lst file in the grub directory, but it is correct, as it has the Windows Vista to boot from (hd0,1).. If I boot through Super Grub Disk and choose to boot from (hd0,1) it boots Vista nicely... Why doesn't it boot from just Grub? 

Here is the menu.lst file:

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
# kopt=root=UUID=dad8e046-b7d7-487c-aae4-3f4834acf813 ro

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dad8e046-b7d7-487c-aae4-3f4834acf813 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dad8e046-b7d7-487c-aae4-3f4834acf813 ro single
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
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```


I'm freaking out, I don't know what else to do... Really weird..! :confused:

Can anyone help please? Thanks in advance.. :)

---

### Post by hermes0710 on 2008-05-09
It seems that you have two entries for vista, one on hd0,0 and the other on hd0,1... Which one is the correct? I suppose the second so choose the second one when grub prompts

---

### Post by eddie_gordo on 2008-05-09
Yes, it has automaticaly added two entries for Vista, but the first one is the Recovery Partition from Asus which is in hd0,0.. But I choose the other one (hd0,1) and it doesn't boot to Vista! :( I cannot understand why it boots from the SGD if I order it to boot from hd0,1 and it doesn't boot from Grub if I order it to boot from hd0,1! :(

Anyone please?!

---

### Post by Pumalite on 2008-05-09
Post:
sudo fdisk -l

---

### Post by eddie_gordo on 2008-05-09
Here it is: 

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69f807c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        4683    35664300    7  HPFS/NTFS
/dev/sda3            6118       14594    68080640    7  HPFS/NTFS
/dev/sda4            4684        6117    11518605    5  Extended
/dev/sda5            4684        4807      995998+  82  Linux swap / Solaris
/dev/sda6            4808        5429     4996183+  83  Linux
/dev/sda7            5430        6117     5526328+  83  Linux

Partition table entries are not in disk order

```

---

### Post by Pumalite on 2008-05-09
You have a Recovery Partition out front. A problem for many. Edit your menu.lst. Leave only one entry for Windows and the 'root' line should be (hd0,1) What do you have in sda3?

---

### Post by eddie_gordo on 2008-05-09
sda3 is a partition for data, where I keep music, videos, etc... I'll try leaving one Windows entry only and give you feedback in a few minutes..

---

### Post by eddie_gordo on 2008-05-09
It didn't work... Now my menu.lst is like this:

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
# kopt=root=UUID=dad8e046-b7d7-487c-aae4-3f4834acf813 ro

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dad8e046-b7d7-487c-aae4-3f4834acf813 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dad8e046-b7d7-487c-aae4-3f4834acf813 ro single
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
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

Anyone? ;)

---

### Post by Pumalite on 2008-05-09
Change 'root' for 'rootnoverify'

---

### Post by eddie_gordo on 2008-05-09
Didn't work either.. :(

Is it me, or I'm the only one who this has ever happened to? lol

---

### Post by Pumalite on 2008-05-09
Change 'root' to (hd0,2)

---

### Post by eddie_gordo on 2008-05-09
As I expected, it didn't work.. :( hd0,2 is my data partition, not the Vista partition... Argh! I'm starting to think I have no solution.. lol

---

### Post by Pumalite on 2008-05-09
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by eddie_gordo on 2008-05-09
Reinstalling Grub won't fix it because this isn't the first time this happens... When I installed Ubuntu 7.10 this happened exactly the same way... Meanwhile I have formated all my hard drive, installed only Vista, and now I have formated it all again and installed Vista and then Ubuntu 8.04 and the problem persists... I don't know what else to do.. :( Is it possible that if I erase the hidden recovery partition from Asus would solve the problem? 

Thanks in advance.. :)

---

### Post by Pumalite on 2008-05-09
If Vista and Ubuntu are to be in the same drive; you have allocate space for Ubuntu with the Vista partitioner first. You cannot partition with the Ubuntu CD.

---

### Post by eddie_gordo on 2008-05-09
Humm... I had some unallocated space and partitioned that space with the Ubuntu CD for Linux.. Could that be the problem? 

Thanks

---

### Post by Pumalite on 2008-05-09
That's fine as long as the 'unallocated' space was obtained through the Vista partitioner.

---

### Post by eddie_gordo on 2008-05-09
I'll try to format it again then... I don't remember where I made that space unallocated.. ;) Thanks for the advice! Then I'll post some feedback.. ;)

---

### Post by Pumalite on 2008-05-09
Install Vista in the whole drive. Then 'shrink' it with the partitioner.

---

### Post by eddie_gordo on 2008-05-10
Well I have formated the partitions destined to Ubuntu in Windows Vista, merged all the unallocated space with the Vista partition, rebooted, and then 'shrank' the partition with Vista to get the unallocated space again, and then with the Ubuntu live CD I have rearranged space to Ubuntu and installed it... The same thing happened, I cannot boot into Windows Vista through Grub, but I can through SuperGrubDisk, choosing the same partition (hd0,1)! I'm getting out of ideas here... I'm thinking on formating the hidden recovery partition from Asus, but I'm not sure if it will solve the problem, and my laptop still has warranty until October.. :(

Any ideas?

Thanks

---

### Post by Pumalite on 2008-05-10
Get rid of Vista and run it in Virtualbox if you have to. You could TrueImage your Vista and pack it away in an external drive, in case you want to go back.

---

### Post by eddie_gordo on 2008-05-10
Yeah, but that's not an option to me, as I need several applications in Windows for school... And I want to run it natively.. :( What is happening in my laptop isn't usual, is it?

---

### Post by Pumalite on 2008-05-10
No, it's not usual. I have Hardy 64 bit even on a Macboook.

---

### Post by eddie_gordo on 2008-05-10
Damn... Maybe I'll stay like this and get in Vista only through SGD.. :( But it's a pain in the *ss! lol

Thanks anyway.. Any ideas let me know please! :)

---

### Post by Pumalite on 2008-05-10
Good luck.

---

### Post by eddie_gordo on 2008-05-12
I managed to find some other people with the same problem as I, and found a solution... **EasyBCD**! Just boot through Windows Vista DVD and repair the MBR through the command prompt 'bootrec.exe /FixMbr' and 'bootrec.exe /FixBoot'.. Then you can just access Vista... Download and install EasyBCD, run it and add a new Entry for Linux.. In that entry check the "Grub isn't istalled" or something like that.. Then reboot and you got two Loaders available... One goes directly to Vista and the other one loads Grub to access Ubuntu! :D

Finally I got my laptop working in dual-boot mode!

Thanks everyone here for the tips and hints!

---

### Post by Pumalite on 2008-05-12
Congrats!

---

### Post by dmj99 on 2008-05-12
I'm a little unsure from looking at your fdisk output where your Vista installation is.  Is it on sda2 or sda3?

If it is on sda2 (the second partition on the disk) then 

```
# This entry automatically added by the Debian installer for a non-linux OS

title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

should work.

If Vista is on the third partition then

```
# This entry automatically added by the Debian installer for a non-linux OS

title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1
```

should work.

---

### Post by eddie_gordo on 2008-05-14
> **dmj99 said:**
> I'm a little unsure from looking at your fdisk output where your Vista installation is.  Is it on sda2 or sda3?

If it is on sda2 (the second partition on the disk) then 

```
# This entry automatically added by the Debian installer for a non-linux OS

title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

should work.

If Vista is on the third partition then

```
# This entry automatically added by the Debian installer for a non-linux OS

title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1
```

should work.

Vista is on the second partition and rootnoverify (hd0,1) does not work.. I know it should, but it doesn't, I don't know why... Well, got it working now... Thanks anyway mates! :D

---

