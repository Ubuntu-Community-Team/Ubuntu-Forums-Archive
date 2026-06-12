---
title: "Install issue: Ubuntu 6.10 won't start, WinXP will"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by cybrkup on 2006-12-28
I'm a brand new linux user, long-time Windows user. BTW, ubuntu rock! Despite the install issue I am dealing with I have been amazed at what a wonderful system it has been. 

Anyway, on to my problem. My basic problem is that U6.10 won't finish booting whenever I have the HDD with winXP enabled. I do not get any error msgs, it just hangs.  XP boots just fine either as a single drive or even with the 2nd disk I have U on. 

I have seen a number of other posts with issues like this, but none seem to match what I am dealing with. At this point I have made so many changes to try and fix this that I am hesistant to proceed with any more changes without expert advice, that means you all.  :) 

Here is my current setup:
[LIST]
[/LIST]Master IDE: WinXP with a seperate partition for Xunbuntu 6.10 and a Swap (I wanted to try linux before doing a full install)
[LIST]
[/LIST]Slave IDE: Ubuntu 6.10 with partitions for /, swap, /home, and a FAT32 partition

As mentioned above, I first setup Xubuntu on a separate partition on my master drive with winxp. That worked great, so I got a second drive and installed Ubuntu without unplugging the WinXp drive (didn't know I needed to at the time). I had also moved Ubuntu to be the master drive and XP to be the slave (I intend to eventually run U as my primary OS). 

Subsequently I switched XP back to be the master and U to be the slave. Right now I can get it to boot to Xubuntu - which I guess happens when it can't find Ubuntu. 

Do I need to do another fresh install with my XP drive disabled? This would be my 4th fresh install, but I will do again if need be. Which drive should be the master and which the slave, and does it really even matter? Ideally I want to be able to use the boot manager to select which OS to boot (not having to disable/enable drives in bios) as my wife also uses the computer so it can't be too complicated.

I am at work right now so I can't include the master.lst and other files I have seen requested, but I was hoping to get some general advice first if possible. Otherwise I will add those later. 

Thanks in advance. 

CybrKup

---

### Post by gustolove on 2006-12-28
if you change which is master and which is slave then the installation for ubuntu would not work because it would be looking on the wrong HDD for the ubuntu installation


you should try switching the hard drives back and see if you can get in...

thats my suggestion...

---

### Post by bulldog on 2006-12-28
To check things we need to know some things.
Even if you can't do this right now,do it when it suites you and post the output of the commands on the forum.
Enter them one at a time in a terminal.
```
sudo fdisk -l  (l as in like)

cat /boot/grub/device.map

cat /boot/grub/menu.lst
```

---

### Post by cybrkup on 2006-12-28
> **gustolove said:**
> if you change which is master and which is slave then the installation for ubuntu would not work because it would be looking on the wrong HDD for the ubuntu installation


you should try switching the hard drives back and see if you can get in...

thats my suggestion...

I changed the master/slave order prior to installing Ubuntu, so it should not have messed anything up...to my way of thinking anyway. And actually I did try reversing both of them even after the install to see if it worked differently, which it did not. 


As for the other file documentation, I will get that later today. 

CybrKup

---

### Post by cybrkup on 2006-12-28
Here is the requested info:

I changed my setup a bit
[LIST]
Master: Ubuntu 6.10 only; multiple partitions[/LIST]
[LIST]
Slave: WinXp + partition with Xubuntu 6.10[/LIST]
[LIST]
Secondary Slave: blank hdd[/LIST]

I intend to eventually get rid of the real windows install and hopefully run XP in virtual mode, so I decided to make Ubuntu the master drive. 

Thanks all so much for helping and please let me know if any other info is needed to help resolve this issue. 

fdisk:
> Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         638     5124703+  82  Linux swap / Solaris
/dev/hda2             639         663      200812+  83  Linux
/dev/hda3             664        7037    51199155   83  Linux
/dev/hda4            7038       24321   138833730    5  Extended
/dev/hda5            7038       17873    87040138+  83  Linux
/dev/hda6           17874       24321    51793528+   b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1           4       32098+  de  Dell Utility
/dev/hdb2   *           5        9126    73272465    7  HPFS/NTFS
/dev/hdb3            9127        9192      530145   82  Linux swap / Solaris
/dev/hdb4            9193        9733     4345582+  83  Linux

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         273     2192841   83  Linux
/dev/hdd2             274        1075     6442065   82  Linux swap / Solaris
/dev/hdd3            1076        6320    42130462+  83  Linux
/dev/hdd4            6321       14593    66452872+  83  Linux
james@Home:~$ 


> james@Home:~$ cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdd



For the menu.lst there was a bunch of other stuff but it was all commented out and looked generic. I will attach a file with the complete text in case I was supposed to include something but didn't.
> 
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd          /initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST



---

### Post by cybrkup on 2006-12-29
Is there any other info needed? I think I got everything.

Thanks again...

CybrKup

---

### Post by bulldog on 2006-12-29
Some questions in return :D 
I like to see your whole menu.lst but that can wait for a moment,there's some info in the top section, which I like to examine.

Do you get a GRUB menu when you're booting from disk hda?
Which partition on hda is your / partition?
Can you give me the output of ```
cat /etc/fstab
```
Why isn't there a windows entry in your menu.lst,if you didn't disconnect the windows disk?
You stated the secondary slave hdd is empty,but I see a linux install,can you clarify this a bit?

---

### Post by cybrkup on 2006-12-29
I will post the entire menu.lst below.

As to your other questions, yes, I get a grub menu on bootup. It gives me the options to either start U or XP.

/dev/hda1 1 638 5124703+ 82 Linux swap / Solaris -- obviously the swap
/dev/hda2 639 663 200812+ 83 Linux -- /boot
/dev/hda3 664 7037 51199155 83 Linux -- /
/dev/hda4 7038 24321 138833730 5 Extended
/dev/hda5 7038 17873 87040138+ 83 Linux -- /home
/dev/hda6 17874 24321 51793528+ b W95 FAT32 / blank, but will be virtual XP one day (hopefully)

> Why isn't there a windows entry in your menu.lst,if you didn't disconnect the windows disk?

I have no clue. I have done the install multiple times to try and fix the problem, so maybe one time I did have the drive with XP disabled. The last time I did the install I did have both drives connected, but maybe it is using something from the past?

> 
You stated the secondary slave hdd is empty,but I see a linux install,can you clarify this a bit?
I had started to install U on this drive but then decided against it so I went out and bought a fresh drive, now HDA. I want to use this 3rd drive for extra storage and playing around; it can be deleted if it makes a difference. 

> james@Home:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=f4e9f50d-3850-488b-af47-6c285d9101c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=32072e7e-add6-42bf-8462-8d43550c2833 /boot           ext3    defaults        0       2
# /dev/hda5
UUID=4cd6b001-e869-4c6a-82f5-23edd5190c18 /home           ext3    defaults        0       2
# /dev/hda1
UUID=c9ff4ec4-fdab-4795-ba57-383fc974b12d none            swap    sw              0       0
# /dev/hdb3
UUID=962ba288-7e55-4925-96c4-fa38a213fa97 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



> james@Home:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f4e9f50d-3850-488b-af47-6c285d9101c4 ro
# kopt_2_6=root=/dev/hda3 ro

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd          /initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2
#title          Microsoft Windows XP Home Edition
#root           (hd1,1)
#savedefault
#makeactive
#map            (hd0) (hd1)
#map            (hd1) (hd0)
#chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb4.
#title          Ubuntu, kernel 2.6.17-10-generic (on /dev/hdb4)
#root           (hd1,3)
#kernel         /boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash 
#initrd         /boot/initrd.img-2.6.17-10-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb4.
#title          Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/hdb4)
#root           (hd1,3)
#kernel         /boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro single 
#initrd         /boot/initrd.img-2.6.17-10-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb4.
#title          Ubuntu, memtest86+ (on /dev/hdb4)
#root           (hd1,3)
#kernel         /boot/memtest86+.bin  
#savedefault
#boot


---

### Post by bulldog on 2006-12-29
If I had the time this could be solved but I should have a lot of questions.
Like why are all the entry commented out on the last menu.lst?

So to save us both a lot of time,I suggest a reinstall of Ubuntu.
This will be done in half an hour of so.
Another question,is there a special reason why you made a separate /boot partition?

Some suggestions.
Install Ubuntu on the master boot device and install GRUB in the MBR with all the drives connected.
To get your fstab up to date automatically it should be advised to partition all your disk before you install ubuntu and reformat them to avoid any confusion with half installed OS's
Referring to the ubuntu disk and the 'blank' secondary slave
For ubuntu,make one 10GB /  (root) partition, a swap about 1GB and the /home to what ever you like.

Make the disk with windows the slave disk,and map your windows entry like this.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1

```
Now will windows boot from the boot loader.
If you want to set windows as the default OS instead of Ubuntu,count the entry's in menu.lst and replace the zero with the number you get when you get to the windows entry.
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0 **<---- this one must be set to the windows entry number**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3
```

---

### Post by cybrkup on 2006-12-29
Ok, reinstall is completed in the manner specified. 

In order to display my complete ignorance I need to ask how I am supposed to make the changes to the menu.lst file. I can open it easy enough via gedit, but it won't let me save any changes. It opens it read-only. I am the admin on the machine and I added myself to the root user group. I have played around with this for a while without success. I need to spend some more time researching this, but if you beat me to that with an answer it would be great.

Also, the menu.lst looked a little different then what you (Bulldog) had entered for the mapping I was supposed to use. I am including the new text below in case anything is wrong.

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
# kopt=root=UUID=b3d1c486-fdcc-423a-88ac-c3c9994625fb ro
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
# on /dev/hdb2
title		Microsoft Windows XP Home Edition
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



---

### Post by bulldog on 2006-12-29
Looks okay to me :D 
I suppose you can boot windows and ubuntu as well from GRUb now?

To do anything to the file system you need to use sudo before the command.
If you want to open an application with a GUI,it's highly recommended to use gksudo instead of sudo.

Example to open your menu.lst to edit it use this,```
gksudo gedit /boot/grub/menu.lst
```
Now you can change what you want and save the file.

If you just want to see a file without changing it you can use ```
cat /boot/grub/menu.lst
```

To see your partitions listed in your terminal you use sudo```
sudo fdisk -l
```

Don't go messing with your root account or what ever,you don't need to do so,if you want root permission for a longer periode 
use ```
sudo -s
``` you can return to the user account using exit.

If you have questions,just ask,in most cases there's someone who can help you.

Some links,

[http://ubuntuforums.org/showthread.php?t=171507](http://ubuntuforums.org/showthread.php?t=171507)

[http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by cybrkup on 2006-12-29
Bulldog,

Thanks again for all the time and tutorials. I'm trying to go slow so I don't muck to much up.

As for your question, it sorta works. If I just boot up my computer it will start loading grub, but then it gives me an Error 22 msg and hangs. I don't get any options to boot anything after that. ](*,) 

If I use my computer's boot menu to boot to my primary drive (HDA) everything works perfectly as I would expect. 

At least that is progress!

CybrKup

---

### Post by bulldog on 2006-12-30
Make the hda first boot device then.:D 
You should realize you have more than once installed ubuntu and grub by doing so.
It means grub can be on several hard disk by now.
So you have to make the disk with the fully functional grub the master when you boot.

---

### Post by cybrkup on 2006-12-30
I should clarify what the problem is. If I reboot and do nothing special I get the grub error. To not get the error I have to select "boot to master drive" upon logon by hitting F12 at startup.

Unfortunately my bios does not allow me to specify which HDD to boot from on a universal basis; I have to select it each time if I am not using the default configuration, so I have to manually change this each time I reboot. I'm not sure what the difference is because theoritically I am booting from the master drive in either instance, but for whatever reason the computer thinks there is a difference. 

Frankly, I'm not going to worry about this right now. I know how to deal with it for now so once I learn more about U-booting I will tackle the issue again. 

CybrKup

---

### Post by cybrkup on 2006-12-30
Nevermind, I just realized why it is doing that. I should be able to fix it easily enough. Consider the issue solved. 

CybrKup

---

