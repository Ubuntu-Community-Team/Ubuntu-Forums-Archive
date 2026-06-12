---
title: "Grub Error 17 woes."
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by penguin666 on 2007-06-14
I have just tried to install Ubuntu on a slave drive dual booting with XP home which was already installed. However when I try to boot from that drive it gets that Error 17 message. At no point do I get any options for which OS to boot. I have read that error 17 means the partition is detected but the filesystem not recognised, will this come up without giving me an OS choice menu if all partitions have a problem or just one of the items on the menu that should be there?

I have tried many of the solutions from this forum and other places but am having no success at all. I have tried:

Changing bios setting for the hard disk mode->auto (already like that) and other option to manual (didn't seem to do much)
Restored GRUB (like it says here: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/))
Tried changing menu.lst (i changed all the hd0's to hd1's)


The situation I have is I only have the 160GB drive on that primary IDE channel (i took the master one off before installing ubuntu so as not to risk anything.) To boot xp from the slave drive I remember I had to change a bios setting from hdd-0 to hdd-1, but then the next time i rebooted I had to change it back to hdd-0, which seemed strange. So I was thinking I was getting this problem cos maybe it is presented to grub as the master even though in the bios when loading it says slave, and when ubuntu has loaded it says its a slave drive. I tried to change device.map from (hd0) /dev/hdb to (hd0) /dev/hda but that made no difference (exactly the same error) so I changed it back.

I don't understand the whole mounting drives and the way numbers and letters are assigned in stuff like hda and hdb but i'm guessing ubuntu knows the drive is a slave as any references to it always are like /dev/hdb.

Here is any information that people ask for, for other similar problems:

```
root@ubuntu:~# fdisk -l

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2189    17583111    7  HPFS/NTFS
/dev/hdb2            2190        2313      996030   82  Linux swap / Solaris
/dev/hdb3           18485       19457     7815622+  83  Linux

```


menu.lst:

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
# kopt=root=UUID=09eef252-e5ae-481e-93ba-0f66f38efdbe ro

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
# defoptions=quiet splash noapic nolapic

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=09eef252-e5ae-481e-93ba-0f66f38efdbe ro quiet splash noapic nolapic
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=09eef252-e5ae-481e-93ba-0f66f38efdbe ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1

```



```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# parted
GNU Parted 1.7.1
Using /dev/hdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            

Disk /dev/hdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  18.0GB  18.0GB  primary  ntfs         boot 
 2      18.0GB  19.0GB  1020MB  primary  linux-swap        
 3      152GB   160GB   8003MB  primary  ext3              

(parted) quit                                                             
Information: Don't forget to update /etc/fstab, if necessary.             



```


fstab (dont really know what this is):

```
root@ubuntu:/etc# cat fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hdb2 swap swap defaults 0 0
root@ubuntu:/etc# 

```


If anybody can help, it would be greatly appreciated as I cant figure out what's going on.

Thanks!

p.s. in the meantime is there anyway to use a floppy disk to kind of jump start it to boot into linux?

---

### Post by confused57 on 2007-06-14
Super Grub Disk might be able to boot your Ubuntu install:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Herman on 2007-06-14
:D Hello penguin666, 
When you unplugged your master hard disk did you notice if you have 'cable select' IDE cables or the other kind where you are supposed to set which hard disk is master and which one is slave by the jumper pins? Is you hard drive set as 'master', slave' or 'cable select' now?

> The situation I have is I only have the 160GB drive on that primary IDE channel (i took the master one off before installing ubuntu so as not to risk anything.) To boot xp from the slave drive I remember I had to change a bios setting from hdd-0 to hdd-1, but then the next time i rebooted I had to change it back to hdd-0, which seemed strange. So I was thinking I was getting this problem cos maybe it is presented to grub as the master even though in the bios when loading it says slave, and when ubuntu has loaded it says its a slave drive. I tried to change device.map from (hd0) /dev/hdb to (hd0) /dev/hda but that made no difference (exactly the same error) so I changed it back.Regards, Herman :D

---

### Post by penguin666 on 2007-06-15
I've checked both drives. The one which was connected as master which is the one ive unplugged has its jumper set as master, and the one in the slave position has its jumper on cable select.



Thanks for the reply!

> **Herman said:**
> :D Hello penguin666, 
When you unplugged your master hard disk did you notice if you have 'cable select' IDE cables or the other kind where you are supposed to set which hard disk is master and which one is slave by the jumper pins? Is you hard drive set as 'master', slave' or 'cable select' now?

Regards, Herman :D

---

### Post by Herman on 2007-06-15
> I've checked both drives. The one which was connected as master which is the one ive unplugged has its jumper set as master, and the one in the slave position has its jumper on cable select.  Aha! Are you using a 'cable select' IDE cable or a plain one? 

A 'Cable select' cable has one blue plug that fits the socket in the motherbboard, and a black plug for your master hard disk. There will be a grey plug for plugging into your slave hard disk.
If you are using 'cable select IDE cables, you should have the jumpers on both hard disks set to 'cable select' position.

If you have an IDE cable that has plugs that are all the same color (black normally) then you have non cable-select IDE cables. You should set your jumper settings to 'Master' for the master drive and 'slave' for the slave hard drive,

Grub will work better if you can get your hardware set up right, then we'll probably need to take a fresh look at your fdisk and menu.lst and we should be able to get everything right then. 
Regards, Herman :D

---

### Post by penguin666 on 2007-06-15
Just checked the cable, and it has a blue plug into the motherboard, but it has two black plugs on the other ends of the cable, although the one in the middle has a label which reads "Ultra ATA Cable, SLAVE".

Just to clarify, I dont have the hard drive which would be in the master position connected, its still unplugged, but does will the bios be remembering things about when it was plugged in?


Thanks


> **Herman said:**
> Aha! Are you using a 'cable select' IDE cable or a plain one? 

A 'Cable select' cable has one blue plug that fits the socket in the motherbboard, and a black plug for your master hard disk. There will be a grey plug for plugging into your slave hard disk.
If you are using 'cable select IDE cables, you should have the jumpers on both hard disks set to 'cable select' position.

If you have an IDE cable that has plugs that are all the same color (black normally) then you have non cable-select IDE cables. You should set your jumper settings to 'Master' for the master drive and 'slave' for the slave hard drive,

Grub will work better if you can get your hardware set up right, then we'll probably need to take a fresh look at your fdisk and menu.lst and we should be able to get everything right then. 
Regards, Herman :D

---

### Post by Herman on 2007-06-15
I'm not too sure.
How about plugging this hard disk in for now with the Master plug then, since it's now the only disk you want to have in the computer for the moment at least. Since Grub looks like it has set itself up to boot Ubuntu as (hd0,2) it should work then, (I hope). 
Let me know what happens! :D I'll be back after I get some sleep.

---

### Post by penguin666 on 2007-06-15
I tried commenting out everything on the GRUB menu.lst apart from the seperator which says "Other Operating Systems", but I still got the same error messages as before, but surely it shouldn't be having any trouble with the partitions if it is not going to load any of them?


I took off the jumper so the drive was set as slave but that didn't do anything, same error, so I put it back onto cable select.

However doing what you said, plugging the drive into the master cable has let it boot up! Thank you!!!

When it loads it still is saying my drive is /dev/hdb even though in the bios it is master, why is that? Is the name /dev/hdb determined by the device.map file which says: (hd0)	/dev/hdb?

Any ideas as to why it wont work when the drive is in the slave position? As I would like to put it there and eventually plug in the other drive to the master position.

Thanks for all the help!!!!!

> **Herman said:**
> I'm not too sure.
How about plugging this hard disk in for now with the Master plug then, since it's now the only disk you want to have in the computer for the moment at least. Since Grub looks like it has set itself up to boot Ubuntu as (hd0,2) it should work then, (I hope). 
Let me know what happens! :D I'll be back after I get some sleep.

---

### Post by confused57 on 2007-06-15
You might consider plugging in your Window's drive as slave...you'd need to make sure the jumper setting is correct(slave or CS), similar to what's described here:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by Herman on 2007-06-15
Hello penguin666, 
I agree with confused57, the how-to confused57 linked you to is a very good way to set up your dual boot in two (or more) hard drives. :D
>  However doing what you said, plugging the drive into the master cable has let it boot up! Thank you!!! No probs! I'm glad it worked. ;)
>  When it loads it still is saying my drive is /dev/hdb even though in the bios it is master, why is that? Is the name /dev/hdb determined by the device.map file which says: (hd0) /dev/hdb? Well I don't know, it's more complicated than that. The device.map is just for Grub. Linux looks at your BIOS seperately from Grub. Linux is still set up for the way you had your hard disk plugged in before. (When you installed).
>  Any ideas as to why it wont work when the drive is in the slave position? As I would like to put it there and eventually plug in the other drive to the master position. I would read confused57's links and delete Ubuntu and re-install it again with both hard disks plugged in and jumpered correctly. It will only take you about half an hour to re-install, that would probably be faster and easier than learning how how to edit /etc/fstab , menu.lst and re-installing Grub and anything else you might have to do to straighten your Ubuntu system all out and get a normal properly configured Ubuntu operating system. Mind you, you would be learning a lot if you decide to do it the long way. :)

The simple, straightforward way to do things is to have your hard disks plugged in and jumpered right, and install Ubuntu in whichever hard disk you want. You can make either hard disk master or slave as you like. Lots of people have Ubuntu installed in a slave drive, it will work fine no matter where you put it.  I agree with confused57, it would be the best to leave the Ubuntu hard disk as master and plug your Windows one in as slave. That way Grub will be installed in the MBR of your Ubuntu disk and the MBR in your other hard disk will be left as it is. It's easy to configure Grub to boot Windows in the second hard disk with Grub's  'map' commands. :D

Programmers have spent years of programming time getting things figured out so you can install Ubuntu in 99.99% of computers and everything will go fine. Honest! :D
There are a few times when people need some help. I might seems like a lot of people in this forum are posting for help with Grub, but remember, almost 1000 people a day are joining Ubuntu Web Forums.
According to the [ubuntu counter project]("http://ubuntucounter.geekosophical.net/"), 15140 users represent  20754 Machines, an average of almost 1.4 machines per user. 
That makes about 1400 installation per day on average if those figures are any indication.
So I think the number of Grub problems per day is very small in proportion to the number of new Ubuntu installations going on around the world. Most Grub or MBR or booting problems are very simple and easily solved.
According to [DistroWatch.com]("http://distrowatch.com/"), Ubuntu is the highest ranked Linux distro in the world with an average of 2843 hits per day over a six month period, (look over in the right column on that page and down a bit).
Therefore I suggest that it's not necessary to bother unplugging any hard drives before installing Ubuntu. Just install normally if you want a normal install.
What you could do if you're worried is make a backup of the IPL part of your first hard disk's  MBR, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").

Above all, have fun, :D
Regards, Herman

---

### Post by confused57 on 2007-06-15
Thanks for all your help, Herman.  Since I wrote up the "HowTo", I've learned much more about grub, due in large part from the grub section on your website and just trying to help new users on the forum, and realize now that it's relatively safe to leave both hard drives connected when installing Ubuntu...I plan on updating the "Tutorial" describing how grub recognizes the (hd0) drive, which is by default where grub's IPL will be installed to the mbr.
Anyone installing on multiple hard drives can choose to install grub to their Windows or Ubuntu drive's mbr, whichever they feel more comfortable installing to.  I might also suggest that anyone planning on installing Ubuntu, burn a copy of the Super Grub Disk first.

---

### Post by penguin666 on 2007-06-15
I guess i'm only having problems because i'm trying to have two drives bootable. Is it common to have problems when trying to use grub on the mbr of the slave drive?

I was originally planning on being able to boot from the different drives by changing in the bios which drive to boot from, however, that doesn't seem to work anymore so i guess ill have to rely on one boot loader for both drives.

Ill give the method confused57 suggested a shot. Although is there any performance hit to windows by booting from a different boot loader?

Is the only thing that will need fixing changing /dev/hdb to /dev/hda? or will that not matter? is that what you meant needed fixing in /etc/fstab?

One last question: I definately have a cable select type ata cable now, so is a correct configuration either both cable select or both set either master or slave? or can you mix them? in other words, do I have to go looking for some tweesers?


Thanks again for all the help Herman and confused57!

---

### Post by confused57 on 2007-06-15
> **penguin666 said:**
> I guess i'm only having problems because i'm trying to have two drives bootable. Is it common to have problems when trying to use grub on the mbr of the slave drive?

I was originally planning on being able to boot from the different drives by changing in the bios which drive to boot from, however, that doesn't seem to work anymore so i guess ill have to rely on one boot loader for both drives.

Ill give the method confused57 suggested a shot. Although is there any performance hit to windows by booting from a different boot loader?

Is the only thing that will need fixing changing /dev/hdb to /dev/hda? or will that not matter? is that what you meant needed fixing in /etc/fstab?

One last question: I definately have a cable select type ata cable now, so is a correct configuration either both cable select or both set either master or slave? or can you mix them? in other words, do I have to go looking for some tweesers?


Thanks again for all the help Herman and confused57!

Setting your system up this shouldn't affect the performance of Windows...it doesn't on 2 different computers I have set up this way.  You shouldn't have to modify anything in your /etc/fstab, since it uses UUID's to mount your Linux partitions.  I think setting both hard drives to Cable Select would be the easiest option...I think you can mix them(one drive CS, the other master/slave).
In bios, are both your hard drive controllers set to "auto" for both hd0 & hd1?  On my Dell, I have to turn the slave drive controller(hd1) to "off" with only one drive connected as master and to "auto" with both drives connected...good luck with getting it working.

---

