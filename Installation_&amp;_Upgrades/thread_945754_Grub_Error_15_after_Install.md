---
title: "Grub Error 15 after Install"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by RomoRock3r on 2008-10-12
I installed Ubuntu 6.10 on a seperate partition on my HDD.I restart and I get Error 15 along with a blinking cursor. I tried re-installing Ubuntu and I get the same error. The CD is ok becuase I installed it before and it worked. Is the menu.lst messed up? 

Here are my Partitions
dev/hda1 Windows Partition (NTFS)
dev/hda2 Ubuntu Partition  (ext3) 
dev/hda3 Swap (linux-swap)

I did fdisk-l and it showed hda1 as boot

Here is my default menu.lst

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
# kopt=root=UUID=c190e5b0-1037-43d8-a6a3-9708ebc8d4eb ro
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
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Any help is appreciated.:KS

---

### Post by caljohnsmith on 2008-10-12
Ubuntu 6.10? Is there some particular reason that you can't use the current 8.04 Hardy version? :)

---

### Post by RomoRock3r on 2008-10-12
I don't want to burn a CD with 8.04 knowing 8.10 comes out in a few weeks. When 8.10 comes out, Ill use that. 6.10 did work fine on this system before.

Specs
1.8ghz P4
256mb RD Ram
160gb HDD
Geforce 6200 256mb
Floppy, Zip drive
DVD/RW

---

### Post by RomoRock3r on 2008-10-13
bump

---

### Post by adrian15 on 2008-10-13
> **RomoRock3r said:**
> I installed Ubuntu 6.10 on a seperate partition on my HDD.I restart and I get Error 15 along with a blinking cursor. I tried re-installing Ubuntu and I get the same error. 

I am not very sure but this link might help you solve your problem:
[http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems](http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems)
Run the: **Super Grub Disk hangs when embeding stage1_5** steps.

adrian15

---

### Post by RomoRock3r on 2008-10-13
Thanks. I was able to install grub to a floppy disk (not super grub) When I select ubuntu to boot, I get Error 17, Cannot mount selected partition. The other options (recovery, memtest) give me error 15. I checked my menu.lst and all the settings are in the right order. Could it be my HDD is messed up? Windows XP wont start up on this system either.

---

### Post by adrian15 on 2008-10-13
> **RomoRock3r said:**
> Thanks. I was able to install grub to a floppy disk (not super grub) When I select ubuntu to boot, I get Error 17, Cannot mount selected partition. The other options (recovery, memtest) give me error 15. I checked my menu.lst and all the settings are in the right order. Could it be my HDD is messed up? Windows XP wont start up on this system either.

Windows XP does not boot? Even using Super Grub Disk Boot Windows option?

You only have one hard disk, don't you?

Maybe testdisk might help you on fixing your partition table scheme although I cannot help you on how to use it.

adrian15

---

### Post by crtlbreak on 2008-10-17
> **RomoRock3r said:**
> Thanks. I was able to install grub to a floppy disk (not super grub) When I select ubuntu to boot, I get Error 17, Cannot mount selected partition. The other options (recovery, memtest) give me error 15. I checked my menu.lst and all the settings are in the right order. Could it be my HDD is messed up? Windows XP wont start up on this system either.

Hello RomoRock3r
It sounds like your boot floppy is possibly not pointing at the boot partition too.

Is that 6.10 a livecd type installation? If not then try get your hands on a livecd or, if you are confident enough, get to a prompt from the text based installation CD
If so then you can easily get to a point where you can start to 

[LIST=1]
[*]back up your data first to separate drive/partition/dvd/usb
[*]attempt to mount the drive under the livecd or text based (prompt) environment
[*]failing the drive mounting at least do some drive diagnostics and file system checks (remember not on mounted drives!) - there are many tools out there - you can even install those tools under the live CD environment (purely for the drive diagnostic)  - obviously these tools will not be available when you reboot in to the livecd.
[/LIST]



let me know how you come along.

Cheers
crtlbrk

---

### Post by RomoRock3r on 2008-10-18
Yes I am using a LiveCD. It was installed from that LiveCD.  I am able to mount the partition from the LiveCD. The menu.lst is taken from the HDD. What are the all diagnostic commands I can use?

I have:

Ubuntu 6.10 LiveCD
Grub Boot Floppy (I made this from the grub installed on my HD)
Super Grub Boot Floppy.

---

### Post by RomoRock3r on 2008-10-25
bump

---

### Post by crtlbreak on 2008-10-28
sorry about delay - I awas out of town - have you checked the file system yet?
sudo fsck /dev/sda
but you can only execute that on an unmounted parition - so from the liveCD.

as an alternate
what I am curious about is why your menu.1st file mentions /dev/hdx rather than a UUID  - so what I see is that yours is possibly a menu.1st from another machine? or possibly the older version of ubuntu used /dev/hdx versus current notation of UUID ?
 otherwise try substituting all the /dev/hdx for your UUID of the hard disk?
this UUID you can obtain from 
sudo cat /etc/mtab
and your partition /dev/hda2 has a UUID number

remember to always make a safety copy of critical files such as menu.1st before editing them - even if the file doesn't work - it is always a good point of reference to return to after much frustration.


let me know how you come along?
regards

---

### Post by RomoRock3r on 2008-11-08
Sorry for the late response, i've been really busy >_>
I downloaded Ubuntu 8.10 and installed it, but I still get Error 15. I believe this is a hard drive problem. It seems as if my computer can read the boot sector at startup but not anything else on the HDD. In my case, It sees Grub on the boot sector and starts it, but after that Grub cant find its own files and then gives error 15. It is the same situation with Windows XP. It sees the bootsector but cant see anything else on the HDD. Thats why I get messages with "files missing cant load windows" right after the POST screen. When I load GRUB on a floppy disk (I made another one with the new install) It is able to load but no matter what option I pick, I get error 15 because Grub cant find the files on the HDD.However I am able to read+write files in my Ubuntu partition from the Live CD . Unless there is a command to "mount" my ubuntu partition then boot off of it, Ubuntu won't work

Here is the menu.lst from the new Ubuntu Installation
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
# kopt=root=UUID=bc6dbab0-8fe5-42f0-aa31-6babcbdc1969 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bc6dbab0-8fe5-42f0-aa31-6babcbdc1969

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		bc6dbab0-8fe5-42f0-aa31-6babcbdc1969
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bc6dbab0-8fe5-42f0-aa31-6babcbdc1969 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		bc6dbab0-8fe5-42f0-aa31-6babcbdc1969
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bc6dbab0-8fe5-42f0-aa31-6babcbdc1969 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		bc6dbab0-8fe5-42f0-aa31-6babcbdc1969
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by fewjr on 2008-11-09
Romorock3r,
I want to thank you for helping me see something I didn't notice before. The UUID entries in menu.lst. Ubuntu Hardy Heron used the root (hd0,x) method whereas Ibex 8.10 uses UUID  XXXXXXX method. I am having a similar problem using Ibex in a dual-boot configuration... see this thread: [http://ubuntuforums.org/showthread.php?t=948327](http://ubuntuforums.org/showthread.php?t=948327). Especially the last page or two. I am going to change those UUID entries to root (hd0,x) entries and see if error 15 goes away. Check that thread to see if it worked. If it does then maybe it will work for you. Hey check out Herman's website here. He has helped us alot. There is alot of great info on there: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I'll try to post here to to let you know if it helped.

Good Luck,
fewjr

---

### Post by meierfra. on 2008-11-09
> GRUB on a floppy disk (I made another one with the new install) It

How did you make the Grub floppy?  From the Grub on the Intrepid Live CD?  I'm asking since versions older versions grub cannot read the 256-inode ext3 file system used by Intrepid.  Edit: Older versions also cannot handle the UIID line in menu.lst.   


Boot from the Grub Floppy and at the grub menu press "c".

Post the output of

```
uuid
```
(uuid will only work with Intrepid's grub)
and 

```
find /boot/grub/stage2
```

Also boot from the Intrepid Live CD and post the output of

```
sudo fdisk -lu
```


Give this a try:

```
sudo grub
```

and at the grub prompt

```
find /boot/grub/stage2 
```
This  will return "(hdX,Y)", where X and Y are some numbers (X should be zero). Then (still at the grub prompt)

```
root (hdX,Y)  # use the numbers  returned by "find"

setup --force-lba (hd0)

quit 
```

Reboot and see whether anything has changed.


Actually I'm pretty much convinced that the problem is caused by your bios and not by grub/ubuntu.  But I want to make sure that we aren't overlooking something.

---

### Post by fewjr on 2008-11-09
I was successful booting Ibex by changing UUID entries in menu.lst to the root (hd0,x) method that earlier versions used. Here are the before and after:

[COLOR="Red"]Before[/COLOR]
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro quiet splash 
initrd	        /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel	        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro  single
initrd	        /boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel	        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



```

[COLOR="red"]After[/COLOR]
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,7)
kernel 	        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro quiet splash 
initrd	        /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,7)
kernel	        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro  single
initrd	        /boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root            (hd0,7)
kernel	        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

It worked like a charm. I'm not sure if it will cause problems updating automagically or not. Chainloading Ibex might be the way to go.

fewjr

---

### Post by meierfra. on 2008-11-09
deleted.

---

### Post by fewjr on 2008-11-09
meiefra,
     Sorry if what I posted was wrong. I was having error 15 problems and thought it might be worth a try. I'm just trying to participate a little.

fewjr

---

### Post by meierfra. on 2008-11-09
> meiefra,
Sorry if what I posted was wrong. I was having error 15 problems and thought it might be worth a try. I'm just trying to participate a little.

fewjr

You must have seen  my post before I deleted it.  I did not want want to critize you,   but merely point  out to RomoRock3r that the UUID's are not the cause of the problem. But then I realized that the "UUID" might actually  play a role when RomoRock3r is booting from the Floppy. (Depends on what version of grub he/she is using on the Floppy). So I delete my second post  and edited my first post.

I learned a lot from your post. I hadn't realized  that UUID's will  cause a problem when using "configfile" from earlier version of grub.

---

### Post by fewjr on 2008-11-09
I wasn't traumatized or anything;). I am really having fun with all this, and I am trying to learn as much as I can with the limited time I have. I operate a Boiler/Chiller Plant, and computers have become my hobby...that and Xboxlive...:lolflag:. Can you say "gain weight".:)

---

### Post by OlJack on 2010-01-16
I just performed a fresh Ubuntu 9.10 install and get the equivalent (dreaded) "blue screen": Grub error 15. The install attempt was on a dual hard drive system.
 
I believe the problem is with the partition tool that comes up during the install. I found the instructions very cryptic and essentially misleading. I believe this tool needs considerably more documentation.
 
To fix the problem I removed the hard drive that should NOT get the OS from the system (unplugged it), then installed, and, after Karmic Koala was up and running, powered down, and plugged the second hard drive in. It all worked fine then because the partitioning tool could not set up the boot wrong with only 1 drive present.
 
I believe the partitioning tool is setting up the discs wrong and the boot data needed by Grub is 1) either placed in the wrong location or 2) Grub is looking for it in the wrong locatioin.
 
The bios is set up so the disk to boot from is Master.
 
All of the fixes involving command-line editing of configuration files etc. that I am seeing in this forum seem to be overkill and presuppose significant knowledge on the part of the installer. I am trying to build an install scenario that can be done by a simple operator... not a system programmer.
 
I believe that, if Linux is ever going to make real inroads in the desktop world (which is what I personally am rooting for) the installs must not require a Phd in rocket science.

---

