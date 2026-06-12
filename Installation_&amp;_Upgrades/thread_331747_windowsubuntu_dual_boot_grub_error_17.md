---
title: "windows/ubuntu dual boot: grub error 17"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by cman on 2007-01-05
I tried to set up a dual boot installation of ubuntu(6.10) and windows xp and now my computer seems to be having trouble booting up.  I get Error 17 from grub every time the computer boots. Here's my info:

**_fdisk -l_**

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        6374    10241437+  83  Linux
/dev/hda3            9539        9729     1534207+  82  Linux swap / Solaris
/dev/hda4            6375        9538    25414830   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001    7  HPFS/NTFS

**_menu.lst_**

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
# kopt=root=UUID=08ae48a4-d10b-457a-b67d-85220b514490 ro
# kopt_2_6=root=/dev/hda2 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


**_device.map_**
(hd0)   /dev/hda
(hd1)   /dev/hdb

Thanks for any help you folks can send my way.

---

### Post by cman on 2007-01-05
is there a better place to ask this question?

---

### Post by bulldog on 2007-01-05
Nope there isn't,you only need someone who knows the answer.

Did have a look at your info,very nice and complete,and I can't see anything wrong at it.
You can't boot windows or ubuntu?

One question though,what's on /dev/hda4 linux?

---

### Post by cman on 2007-01-05
Nope, can't boot either of them.  /dev/hda4 is /home I think.  This is the first time I've used Linux, so it's possible I mucked something up in the install, but it seemed fairly straightforward.  This is the second install attempt. The first one gave me the same results so I reinstalled it to be sure it wasn't an error in the install.

---

### Post by bulldog on 2007-01-05
Well if you want to make a /home call it /home :D 
Let's reinstall GRUB to see what GRUB has to say,but I think you have two ubuntu's and no /home.
You have to boot into the live ubuntu cd to accomplish this,
When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

If this gives not the desired solution we'll take a further look at your linux partitions.
So we can see what folders are on this partitions,I'm currently only interested in the answer you get from the find /boot/grub/stage1 question.

---

### Post by logos34 on 2007-01-05
[cancel]

---

### Post by cman on 2007-01-05
the boot grub stage1 command gave me: (hd0,1)

still no luck.  im still getting:

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17

---

### Post by quartzy on 2007-01-06
/dev/sda is the primary boot HDD in your bios?

---

### Post by bulldog on 2007-01-06
> **cman said:**
> the boot grub stage1 command gave me: (hd0,1)

still no luck.  im still getting:

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17
(hd0,1) is correct.
Can you give me the fstab```
cat /etc/fstab
``` to see if your ubuntu is properly listed there as well?

---

### Post by cman on 2007-01-06
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=08ae48a4-d10b-457a-b67d-85220b514490 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=555193f4-9781-40f8-9344-2368a78f8162 /home           ext3    defaults        0       2
# /dev/hdb1
UUID=64C42589C4255E94 /ntfs-storage   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=1044501B445005BE /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=cb4e7278-1384-43a7-bb4a-559242a3b202 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by bulldog on 2007-01-06
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda2
UUID=08ae48a4-d10b-457a-b67d-85220b514490 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda4
#UUID=555193f4-9781-40f8-9344-2368a78f8162 /home ext3 defaults 0 2 **<----- did you mount this one as /home?**
# /dev/hdb1
UUID=64C42589C4255E94 /ntfs-storage ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda1
UUID=1044501B445005BE /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda3
UUID=cb4e7278-1384-43a7-bb4a-559242a3b202 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
```

Put a # before the line with my remark and save it.
Try again to boot ubuntu and see what happens.

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

This is what error 17 means,everything is okay but can't recognize a file system.
The question would be,file system from which partition?
So comment out your sda4 and see what happens.

---

### Post by cman on 2007-01-06
Still getting error 17.  Is there another bootloader I can use or some other way to boot into Linux without GRUB?

---

### Post by bulldog on 2007-01-06
Well there should be other boot loaders like Lilo but if GRUB can't boot I suppose another one can't either.
All the settings are alright,so can't say what's wrong with the file system.

---

### Post by Sonicgoo on 2007-01-06
Hello 

I am having similiar problems; I have made a mess, your help is appreciated. 

I'm trying to install Windows 2000 and Ubutnu as a dual boot. 

**Here is my Menu.lst.**
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
# root		(hd1,1)
# kernel	/vmlinuz root=/dev/hdb2 ro
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
# kopt=root=/dev/hdb2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hdb1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2  quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2  single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

**and Here is my fdisk**

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         513     4120641    7  HPFS/NTFS
/dev/hda2             514        1026     4120672+   f  W95 Ext'd (LBA)
/dev/hda5             514        1026     4120641    6  FAT16

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4111    33021576    c  W95 FAT32 (LBA)
/dev/hdb2   *        4112        4830     5775367+  83  Linux
/dev/hdb3            4831        4866      289170    5  Extended
/dev/hdb5            4831        4866      289138+  82  Linux swap / Solaris

**Here is a cat fstab**

ubuntu@ubuntu:~$ sudo cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hdb5 swap swap defaults 0 0
ubuntu@ubuntu:~$

---

### Post by EugeneK on 2007-01-07
.

---

### Post by EugeneK on 2007-01-07
> **Sonicgoo said:**
> Hello 

Idiot redneck. 

;)

---

### Post by EugeneK on 2007-01-07
My 'Blab reply, sonicgoo:

One problem is that your root partition for ubuntu in your menu.lst has the wrong syntax:

title Ubuntu, kernel 2.6.15-23-386
root (hdb1,1)

should be
root (hd1,1)

 btw, you can edit this when grub comes up by pressing 'e', instead of editing menu.lst itself

And that fstab file is the fstab for your live CD. Hopefully, the one on your hard drive will work once you get past grub. But if there's problems, and you want to see it from the live CD, you'll need to have the hard drive's linux partition mounted. I don't think the live CD does that for you automatically, so here's how to do it manually:

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/hdb2 /ubuntu

You can then cat /ubuntu/etc/fstab

---

### Post by Sonicgoo on 2007-01-21
I still have had no luck booting Ubuntu from a hard drive with this so far. 



So here is the cat fstab after that. 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


here is the fdisk -l
  Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4111    33021576    c  W95 FAT32 (LBA)
/dev/hdb2   *        4112        4830     5775367+  83  Linux
/dev/hdb3            4831        4866      289170    5  Extended
/dev/hdb5            4831        4866      289138+  82  Linux swap / Solaris

---

### Post by Sonicgoo on 2007-01-21
My current menu.lst

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
default		0_sequence

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
# root		(hd1,1)
# kernel	/vmlinuz root=/dev/hdb2 ro
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
# kopt=root=/dev/hdb2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-26-386
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

