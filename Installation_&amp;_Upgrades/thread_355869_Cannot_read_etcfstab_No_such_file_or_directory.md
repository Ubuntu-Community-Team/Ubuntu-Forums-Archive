---
title: "Cannot read /etc/fstab: No such file or directory"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by cnc333 on 2007-02-07
I have a dual boot system that started giving me problems when I upgraded from on board video to a pci-express card. Origionally, when i booted into ubuntu i would get an error, about the video, asking me if i wanted to look at a certain file (i cant remember which file it is now, but i think it had somthing to do w/ x11 or something). eventually i would get to a command prompt type enviroment w/ my normal terminal heading. i would just type ```
sudo -s
reboot
``` and go back onto windows and on my merry way. well, i finally decided i was going to go into and do something along the lines of ```
sudo dpkg-reconfigure -phigh xserver-xorg hd(0,1)
``` and install the right drivers for my new vid card (a geforce 6200)


WELL.... now when i boot into ubuntu i get the following ```
....
blah.....
blah....
blah....

mount:
Cannot read /etc/fstab: No such file or directory
mount: Mounting /root/dev on dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

I havent changed anything with the partitions or grub. ive tried searching but havent found anything applicable. any help is appreciated and tia

cnc333

---

### Post by taurus on 2007-02-07
If you somehow accidentally deleted /etc/fstab, you need to create a new one.  Boot from the LiveCD and post the output of this command here?

```
sudo fdisk -l
```

---

### Post by cnc333 on 2007-02-07
ok, let me dig out one of my discs. ill brb

---

### Post by cnc333 on 2007-02-07
exactly which part do you need, i dont have an easy to copy and i dont want to type the whole thing unless i have to

---

### Post by cnc333 on 2007-02-07
```

&#65279;ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7116    57159238+   7  HPFS/NTFS
/dev/sda2            7117        8276     9317700   83  Linux
/dev/sda3            8277        8331      433786+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4            8331        9729    11237436    b  W95 FAT32
/dev/sda5            8277        8330      433692   82  Linux swap / Solaris

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       33814   271610923+   7  HPFS/NTFS
/dev/hda2           33815       38913    40957686    7  HPFS/NTFS
ubuntu@ubuntu:~$

```

---

### Post by cnc333 on 2007-02-07
bump

---

### Post by taurus on 2007-02-07
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
/dev/sda2        /               ext3    defaults,errors=remount-ro      0       1
#
/dev/sda5       none                swap    sw              0       0
#
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/             /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by cnc333 on 2007-02-07
im not sure what you want me to do with this...
i would show you mine, but im not sure how to do it with the live cd, it doesnt look anything like that one. im still a noob

---

### Post by cnc333 on 2007-02-07
ok i figured out how to get to my hd from live cd and here are the /etc/fstab and i also included the /boot/grub/menu.lst


/etc/fstab: ```
&#65279;# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/dvdrecorder   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/dvdrecorder-1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda5       /media/windows  vfat  iocharset=utf8,umask=000  0    0
/dev/hda1       /media/bigstorage  ntfs-3g defaults,locale=en_US.utf8   0    0
/dev/hda2       /media/storage  ntfs-3g defaults,locale=en_US.utf8   0    0
/dev/sda4        /media/fat32   vfat user,noauto     0       0


```

/boot/grub/menu.lst```
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
# kopt=root=/dev/sda3 ro

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

hope this helps in my diagnosis and tia. if there isnt a quick reply, it will be in the morning before i can get on again. its time to hit the hay.
cnc333

---

### Post by warkro on 2007-02-08
i think he wants you to make a new /hdX/etc/fstab 
```
sudo gedit /hdX/etc/fstab
```

hdX is where your ubuntu is
and paste the following.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
/dev/sda2        /               ext3    defaults,errors=remount-ro      0       1
#
/dev/sda5       none                swap    sw              0       0
#
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/             /media/floppy0  auto    rw,user,noauto  0       0
```

If you want to mount your other partitions just reply back

EDIT:  Nevermind, it looks like you already have the right fstab.

---

### Post by cnc333 on 2007-02-08
so if my fstab looks right then what do i do next? im clueless here. thanks for any help.

---

### Post by cnc333 on 2007-02-09
hello... is anyone out there.. im really desperate here :\

---

### Post by confused57 on 2007-02-09
What you can try, in the grub menu at bootup, is make sure the entry to boot Ubuntu is highlighted, press "e", to edit, and on the kernel line where it has root=/dev/sda3, change it to root=/dev/sda2...then press "b" to boot.  May or may not work, worth a try.

I'm suggesting this because your original "fdisk -l" shows sda2 as your Linux partition(presumably root /), however, your /etc/fstab shows /dev/sda3 and your kernel line also shows sda3...if your fdisk -l is correct, then root=/dev/sda2 should boot Ubuntu...see what happens & we'll go from there.

---

### Post by cnc333 on 2007-02-09
ill give it a try in a few min or in the morning, im burning a disc right now. 

i jus noticed that youre from NC.. so am i.. pretty cool that someone from 'round here knows how to use linux, lol. j/k im about 60-ish miles west of ya in elkin, wilkesboro area.

---

### Post by confused57 on 2007-02-09
> **cnc333 said:**
> ill give it a try in a few min or in the morning, im burning a disc right now. 

i jus noticed that youre from NC.. so am i.. pretty cool that someone from 'round here knows how to use linux, lol. j/k im about 60-ish miles west of ya in elkin, wilkesboro area.

There's quite a few forum members from NC...There's several nice golf courses in the Elkin area, I've played High Meadows & Ole Beau... they're pretty tough, though.
Nice to meet you, you'll be up-to-speed in no time with Ubuntu.

---

### Post by cnc333 on 2007-02-09
yeah, ceadarbrook is the local good one. im not a big golfer at all but my uncle lives for it. he some times works at roaring gap... if u know olf beau u know roaring gap.  

anyway.. back to ubuntu. switching grub to /sda2 worked for me then i went in and ```
sudo dpkg-reconfigre -phigh xserver-xorg
sudo -s
reboot
```
and all is working like it used to.   i understand how to edit my menu.lst to fix the /sda2 but i dont understand WHY it changed on me. ive done nothing to change my hardware config and ive not been in ubuntu enough to even start to mess w/ it. oh well, its working now. thanks for everyones help

---

### Post by confused57 on 2007-02-10
> **cnc333 said:**
> yeah, ceadarbrook is the local good one. im not a big golfer at all but my uncle lives for it. he some times works at roaring gap... if u know olf beau u know roaring gap.  

anyway.. back to ubuntu. switching grub to /sda2 worked for me then i went in and ```
sudo dpkg-reconfigre -phigh xserver-xorg
sudo -s
reboot
```
and all is working like it used to.   i understand how to edit my menu.lst to fix the /sda2 but i dont understand WHY it changed on me. ive done nothing to change my hardware config and ive not been in ubuntu enough to even start to mess w/ it. oh well, its working now. thanks for everyones help

I don't understand why your root designation changed, especially since you didn't change anything or repartition...you might want to read over this link:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

I noticed that your menu.lst has:
# kopt=root=/dev/sda3 ro

When there's a kernel update, update-grub uses this line and the groot line to update your new kernel entries in your menu.lst.

Thanks, I'll have to look into Cedarbrook...

---

### Post by cnc333 on 2007-02-10
ok, yeah. # kopt=root=/dev/sda3 ro would make sence. before you said this, or at least before i read this post i was going to reply and mention that it appears to be everytime i get a kernel update. reason being.. after i played in linux a while and rebooted to windows it didnt default into it. I may have changed my default boot since the menu.lst i posted, but i have it set on 10.  instead of windows, this time it booted into memtest.  i started looking and it had a kernel update. so now on this computer i have:
2.6.15-23-386
2.6.15-25-386
2.6.15-26-386
2.6.15-27-386
2.6.15-28-386 
and recoveries for each one. 

i havent read the link yet, cuz i just seem to be so damned tired here lately, but i will tomorrow. but my understanding is that i can change # kopt... to # kopt=root=/dev/sda2 and everything will work fine? if thats not right let me know. i wont make any changes until i read the link though. THANKS FOR YOUR HELP.

---

### Post by cnc333 on 2007-02-10
you know, this problem may stem from something similar to the same problem as the last thread that i opened. or at least be the reminants of the last config since i didnt know to change everything the right way... just a thought

---

