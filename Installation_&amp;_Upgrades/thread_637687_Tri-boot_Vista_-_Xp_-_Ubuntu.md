---
title: "Tri-boot Vista - Xp - Ubuntu"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by techgeek40 on 2007-12-11
I have three hard drives (dev listed below)
Partition the drives just fine - no problems
When I install Ubuntu I see the sda1 (which is my Vista) sda2 (which is my XP)
I then use Ubuntu's partition on the "third" partition to make a swap file - that goes fine.
Then I use the remaining partition (listed as free in Ubuntu) to install the O/S

I have tried the ReiserFS and ext3 (though I don't know what the difference would really be)

Here is the screen I get for Step 7 of 7 

Language: English
Keyboard layout: U.S. English
Name: techgeek
Login name: techgeek
Location: America/New_York
Migration Assistant:

If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
partition #3 of SCSI1 (0,0,0) (sda) as swap
partition #4 of SCSI1 (0,0,0) (sda) as ext3

That's where I am running into a problem.

Addendum:

Okay,
Here is how I have things laid out

DEVICE TYPE MOUNT POINT FORMAT? SIZE USED
/dev/hda
/dev/hda1 ntfs /media/hda1 (76720 MB) 7600 MB
/dev/hda2 ntfs /media/hda2 (5241 MB) 1100 MB
/dev/hdc
dev/hdc1 ntfs /media/hdc1 (80023 MB) UNKNOWN
/dev/sda
/dev/sda1 ntfs /media/sda1 (59290 MB) 17800 MB
/dev/sda5 ntfs /media/sda5 (24594 MB) 6000 MB
/dev/sda3 swap (1998 MB) 0 MB
/dev/sda4 ext3 / (74150 MB) 3500 MB
/dev/sdb
/dev/sdb1 ntfs /media/sdb1 (80077 MB) 24800 MB
/dev/sdb2 ntfs /media/sdb2 (79961 MB) 63500


As you can see I am using sda4 for the Ubuntu install - so my question is how do I get EasyBCD to see that and us it?

Addendum:

This is the error I get when I install

Unable to install GRUB in (sda4)
Executing 'grub-install (sda4)' failed.
This is a fatal error

Now I did get a post from another forum that I should use it as (hd0,3)
But why that? I know I'm not understanding this but the hd0,3 - the 3 would be my swap file?

---

### Post by techgeek40 on 2007-12-11
Update
I did try the install on (hd0,3) and still got the same error
I'm not understanding why
I know the hd stands for hard drive - I don't know what the 0 would mean - the three is the install itself

I really need some help understanding this and getting it working

Thank you

Richard

---

### Post by confused57 on 2007-12-11
The numbering in grub starts at 0, so (hd0,3) would be hard drive #1, partition #4; however, (hd0,3) may be your Windows drive.  It would be best to install grub to /dev/sda4, which you can enter manually(after you press the "Advanced" button) in the box containing (hd0).

Here's a guide for EasyBCD, if you don't already have it:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by logos34 on 2007-12-11
[delete - confused57 was quicker on the draw this time]

---

### Post by techgeek40 on 2007-12-11
Here is what I am NOT understanding.
I am not installing on the "first" hard drive (hd0)

Here's that list again:

/dev/hda
/dev/hda1 ntfs /media/hda1 (76720 MB) 7600 MB
/dev/hda2 ntfs /media/hda2 (5241 MB) 1100 MB
/dev/hdc
dev/hdc1 ntfs /media/hdc1 (80023 MB) UNKNOWN
/dev/sda
/dev/sda1 ntfs /media/sda1 (59290 MB) 17800 MB (Vista install)
/dev/sda5 ntfs /media/sda5 (24594 MB) 6000 MB   (XP Install)
/dev/sda3 swap (1998 MB) 0 MB
/dev/sda4 ext3 / (74150 MB) 3500 MB (Where I want Ubuntu)
/dev/sdb
/dev/sdb1 ntfs /media/sdb1 (80077 MB) 24800 MB
/dev/sdb2 ntfs /media/sdb2 (79961 MB) 63500

So looking at this - the /dev/sda4 - how is (hd0) the sda4 drive (where ubuntu is being installed on)
SDA is the third hard drive in the series if I am reading this right

I know I have asked this so I will ask again - to make me understand.
hd0,3 --- the 3 stands for the partition number? 

> **confused57 said:**
> The numbering in grub starts at 0, so (hd0,3) would be hard drive #1, partition #4; however, (hd0,3) may be your Windows drive.  It would be best to install grub to /dev/sda4, which you can enter manually(after you press the "Advanced" button) in the box containing (hd0).

Here's a guide for EasyBCD, if you don't already have it:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by confused57 on 2007-12-11
Here's a quick guide to grub's numbering system:
[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

For EasyBCD to boot Linux, grub has to be installed to the root partition, which in your case appears to be /dev/sda4...rather than using something like installing grub to (hd2,3), it is best to use "/dev/sda4", again without quotes.  I think there is an "Advanced" button at step7 that you need to click on, which will give you the ability to type in /dev/sda4, in place of the default (hd0).

---

### Post by techgeek40 on 2007-12-11
I am going to do that when I get home but here is some more.


Let me post it this way; because I may be leaving something out.

I started this whole thing in this order:

1)Installed Vista (/dev/sda1) rebooted several times – all worked.
2)Installed XP (/dev/sda5) rebooted several times – all worked.
3)Put in the Vista CD – fixed MBR
4)Back in Vista, installed the EasyBCD and set up the Dual boot fuction. That worked fine and I was able to boot into either Vista or XP
5)Shut down, rebooted with the Ubuntu Live CD and got in just fine. Started installation process. At step 7 of 7, I did NOT change the (hd0) leaving that alone. Everything went fine, no errors.
6)Went back into Vista, started up EasyBCD and selected the Linux tab, selected Grub (now, the foggy part is I don't remember all of the options I may have choosen.)
7)Rebooted, did see the “Ubunut” boot and selected, but got some errors and wasn't able to even load Ubuntu – I had to shut down and go back into Vista. That is where I went into Computer Management and deleted the two partitions to try over.

That is when I started trying to use hd0,2 or hd0,3 and that is when I would ge the errors:
Unable to install GRUB in (sda4)
Executing 'grub-install (sda4)' failed.
This is a fatal error 

Below is my full drive layout. (More below that)

DEVICE TYPE MOUNT POINT FORMAT? SIZE USED
/dev/hda
/dev/hda1 ntfs /media/hda1 (76720 MB) 7600 MB
/dev/hda2 ntfs /media/hda2 (5241 MB) 1100 MB
/dev/hdc
dev/hdc1 ntfs /media/hdc1 (80023 MB) UNKNOWN
/dev/sda
/dev/sda1 ntfs /media/sda1 (59290 MB) 17800 MB (Vista)
/dev/sda5 ntfs /media/sda5 (24594 MB) 6000 MB (XP)
/dev/sda3 swap (1998 MB) 0 MB (Swap – obvious)
/dev/sda4 ext3 / (74150 MB) 3500 MB (Ubuntu)
/dev/sdb
/dev/sdb1 ntfs /media/sdb1 (80077 MB) 24800 MB
/dev/sdb2 ntfs /media/sdb2 (79961 MB) 63500

Now, I did check NeoSmarts forums and did what was suggested, even using the step by step guide, nada.

So, there it is – in a nutshell. I have looked all over the web and it seems there are those that are doing triple boot and making it sound easy, but yet no details of how they are doing it.

That's it in a nutshell

---

### Post by techgeek40 on 2007-12-11
Is it possible to type in /dev/sda4 in the advanced area of step 7?

> **confused57 said:**
> Here's a quick guide to grub's numbering system:
[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

For EasyBCD to boot Linux, grub has to be installed to the root partition, which in your case appears to be /dev/sda4...rather than using something like installing grub to (hd2,3), it is best to use "/dev/sda4", again without quotes.  I think there is an "Advanced" button at step7 that you need to click on, which will give you the ability to type in /dev/sda4, in place of the default (hd0).

---

### Post by confused57 on 2007-12-11
> **techgeek40 said:**
> Is it possible to type in /dev/sda4 in the advanced area of step 7?
Yes, this is what I was suggesting:
> The numbering in grub starts at 0, so (hd0,3) would be hard drive #1, partition #4; however, (hd0,3) may be your Windows drive. It would be best to install grub to /dev/sda4, which you can enter manually(after you press the "Advanced" button) in the box containing (hd0).

You might want to boot your Ubuntu live cd and mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
The post the /boot/grub/device.map and /boot/grub/menu.lst files...for you menu.lst, you just need to copy & paste the boot entries.  It's possible that grub isn't detecting the correct hard drive boot order in bios...your device.map will show how grub recognizes your boot order.

---

### Post by techgeek40 on 2007-12-11
Well, I used the /dev/sda4
No errors
Went to Vista and EasyBCD and under the linux option choose GRUB and all the happy stuff (Type Grub - Name Neosmart Linux - Drive Partition 3 (linux native)

But here is the error I get:

LOADING NEW PARTITION
BOOTSECTOR FROM C.H. HOCHSTATTER

CANNOT LOAD FROM HARDDISK
INSERT SYSTEMDISK AND PRESS ANY KEY

(I press enter - no other boot disk and I get)

BOOT FROM CD (I hit enter)
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

---

### Post by techgeek40 on 2007-12-12
> **Computer Guru said:**
> I had no idea you could type "/dev/sda*" in the advanced box and get it to work - have you tried it?

OKay, I am using ubuntu
BUT -----

Is there a way to make a "text" file so that it will record all boot loading processes

I get the boot options - but I have to choose Windows - and then cycles through - gets back to the boot options - and then I can get into Ubuntu - if I do it any other way it just cycles through.

Just curious if there is a way to make a log of everything going on to "boot" and then post that

(UPDATED INFORMATION)
Now this is strange. I went into the BIOS and reset to optimal settings - rebooted. Now, I had at first used the Vista CD to repair the boot record, and rebooted. But "grub" still loaded. So I said, what the hell, and hit enter - no errors and Ubuntu loaded with NO issues.

Scratching head - Okay - my maxtor HD is the first drive loading - but that is a "extra" drive I use to store audio/home movies on - not a boot loader - what the ??????

I'm a tech - Windows / PC - not "Ubunut" so I'm NOT about to complain. I have learned that sometimes, things just work.

---

### Post by techgeek40 on 2007-12-12
It was suggested I edit /boot/grub/menu.lst 

Where would I find that? And what would I edit in it?

---

### Post by confused57 on 2007-12-12
> **techgeek40 said:**
> Well, I used the /dev/sda4
No errors
Went to Vista and EasyBCD and under the linux option choose GRUB and all the happy stuff (Type Grub - Name Neosmart Linux - Drive Partition 3 (linux native)

But here is the error I get:

LOADING NEW PARTITION
BOOTSECTOR FROM C.H. HOCHSTATTER

CANNOT LOAD FROM HARDDISK
INSERT SYSTEMDISK AND PRESS ANY KEY

(I press enter - no other boot disk and I get)

BOOT FROM CD (I hit enter)
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
I believe EasyBCD(Vista's bootloader) is trying to boot the wrong hard drive.  You can mount your root partition, using the Ubuntu live cd...open a terminal(Applications---Accessories---Terminal):
```
sudo fdisk -l
```
the -l is a small "L"
This should list your hard drives & their partitions, if your Ubuntu root partition is /dev/sda4, then:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda4 /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
```

Post the boot entries in your menu.lst and the entire device.map file...

You can always use the Ubuntu live cd to install grub to the mbr of your Ubuntu drive:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Read the instructions in the thread, but you would do something like:
```
sudo grub
find /boot/grub/stage1
```
Use the results of "find /boot/grub/stage1" to reinstall grub to the Ubuntu drive's mbr, e.g.:
```
root (hd2,3)
setup (hd2)
quit
```

Then set your bios to boot first to the Ubuntu drive...if you get a grub boot menu, highlight your Ubuntu entry, press "e" to edit, highlight the line with root, change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot...y means leave this value as it is.  This is a temporary change, but can be made permanent, if it works.  You may want to try adding entries to grub to boot Vista & XP.

---

### Post by techgeek40 on 2007-12-12
Okay I did as you suggested
Now, the strange this is this (I will post the copies of the text files I made in a few)

I highlighted the Ubuntu entry, and pressed "e" (root)
I changed the (hd2,3) to (hd0,3) and then "b"
Booted - not one error.

Now the strange part is when I did
find /boot/grub/stage1
I got back the hd2,3

Following the advice of that web page ([http://ubuntuforums.org/showthread.php?t=224](http://ubuntuforums.org/showthread.php?t=224))
I did exactly what it said - still got an Error 22 : partition not found (or something like that)

So I went through the steps you gave (the "e" and "b") and got in
LOL The only problem now is that my Vista/XP options are not showing up - but I'm going to read on how to get them into the boot loader; though technically I should be able to put in my Vista CD and just "repair" the MBR and redo the EasyBCD part - at least for Vista and XP

---

### Post by techgeek40 on 2007-12-12
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce21ce21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7209    57900776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7209       10199    24018089    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           10200       10442     1951897+  82  Linux swap / Solaris
/dev/sda4           10443       19457    72412987+  83  Linux
/dev/sda5            7209       10199    24018088+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce60ce60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9736    78201153    7  HPFS/NTFS
/dev/sdb2            9736       19458    78087168    7  HPFS/NTFS

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd51dd51

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9328    74921984    7  HPFS/NTFS
/dev/hda2            9328        9965     5118976    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xbce1bce1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       10337    78147688+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by techgeek40 on 2007-12-12
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
# kopt=root=UUID=a8f235c9-34c9-4623-bdb5-3f291f57a5be ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,3)

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
root		(hd2,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a8f235c9-34c9-4623-bdb5-3f291f57a5be ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a8f235c9-34c9-4623-bdb5-3f291f57a5be ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,3)
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
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by techgeek40 on 2007-12-12
(hd0)	/dev/hda
(hd1)	/dev/hdc
(hd2)	/dev/sda
(hd3)	/dev/sdb

---

### Post by confused57 on 2007-12-12
Here's something you may want to try, boot into Ubuntu by highlighting the Ubuntu entry & pressing "e", etc...once you've booted into Ubuntu, open a terminal & add another Vista entry in your menu.lst:
```
cd /boot/grub
gksudo gedit menu.lst
```

Add another Vista entry below your current entry:
```
title Windows Vista/Longhorn (loader) Test
root (hd0,0)
savedefault
makeactive
chainloader +1
```
quit & save...note: not sure if you need the makeactive line.

Then reboot your computer, booting first to the drive with Ubuntu, then select Vista...Test  in the grub boot menu.

If this works, you can make the changes permanent in your /boot/grub/menu.lst.

---

### Post by techgeek40 on 2007-12-13
Now, the only thing I have to find is a way to add the boot options (and to get into) Vista and XP - (my wife will kill me if she can't get into Vista)

---

### Post by techgeek40 on 2007-12-13
I did as you suggested (for Vista)
But it wouldn't load - giving me an error that there was a problem with the MBR
So I reset the bios back to the sata drive that has the three OS's on them to first - 
Now, I have to tell it to go to the Ubuntu boot loader - it just 're-displays' what I had - but then I can select the Vista OS

(Pulling hair out)

LOL Okay - where is the tech support number LOL

Damn I need someone who can be on the phone and I can explain what happens as it happens - oh the pipe dreams

---

### Post by confused57 on 2007-12-13
I understand what's going on with Ubuntu & grub, by your device.map:
```
(hd0) /dev/hda
(hd1) /dev/hdc
(hd2) /dev/sda
(hd3) /dev/sdb
```
Is this the bios boot order when you installed Ubuntu?  Regardless, grub recognized /dev/sda as (hd2), the 3rd hard drive in the boot order...unless you specify otherwise, grub is installed by default to (hd0) or /dev/hda.  When you set bios to boot first to your Ubuntu drive(sda), it in effect became (hd0), which is why changing the root designation enabled you to boot Ubuntu.

I don't know enough about Vista & XP to know if their IPL is installed to the first hard drive's mbr.  I've read on MSes site that they recommend installing older versions of Windows first in a dual boot with a later version; however, the later version(Vista) overwrites the XP bootloader.  However, installing this way, I've read it's not possible to remove either version of Windows and have the other one bootable. The method you used sounds like it worked great.

I don't know if  when you set up EasyBCD, you need to select Drive#2, Partition#3 in order to boot Ubuntu, if this is your bios boot order?

You probably already know how to use the bootrec.exe utility on the Vista install DVD:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

Sorry I can't help you more, with  my lack of knowledge dualbooting Vista & XP on a pc with multiple drives, I don't really feel qualified to give you specific advice.

I don't know if hiding one Windows from another in grub would help or not:
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk)

---

### Post by techgeek40 on 2007-12-13
I have GOT to thank everyone who helped me with this - there is NOT a big enough THANK YOU in the world.

I have it working - and even "edited" the GRUB so that "Vista" is the first on the list with a warning that it's for all users (I have to - I have a wife - I do like breathing, you know :>)

So, everything is working - and even edited the grub so that Ubuntu now boots with no errors - booting off of (hd0,3) 

Makes sense? Nope - 

Tune in next week when techgeek figures out how to tie his shoe laces and gets a cookie

(You know - I'm actually starting to understand this)


Now, on the other side:
I would like the grub to boot right into Vista. Right now, as it stands, I highlight the (Vista (Loader) Test (though I did edit that part) and it then takes me to the "EasyBCD" boot options window where one would have to either select Vista or Xp

If anyone can figure out how to get around that - so I can have just in the grub Vista and/or XP load - that would be awesome.

---

### Post by confused57 on 2007-12-13
Great job getting it working, your perseverence paid off...You may have already done so, but the Vista entry needs to be above the ###BEGIN AUTOMAGIC KERNELS LIST, as described in this thread:
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk)
I have to keep the wife happy also, so the pc boots into Windows by default.

I assume you've permanently changed the grub entries in your menu.lst to (hd0,3)...you also need to change the line with #groot to (hd0,3):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
If you have a kernel update, update-grub is run, which would change your root back to what is listed in groot.

Added:  By the way, what changes did you make in your Vista grub entry in order to get Vista/XP to boot/

---

### Post by techgeek40 on 2007-12-13
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
# kopt=root=UUID=a8f235c9-34c9-4623-bdb5-3f291f57a5be ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,3)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		WINDOWS VISTA (ALL USERS) HIGHLIGHT THIS AND HIT ENTER
root		(hd0,0)
savedefault
makeactive
chainloader	+1

### BEGIN DEBIAN AUTOMAGIC KKERNELS LIST

title		UBUNTU (7.10) (DO NOT ENTER - FOR RICHARD ONLY)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a8f235c9-34c9-4623-bdb5-3f291f57a5be ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		UBUNTU (7.10) (RECOVERY MODE - ONLY)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a8f235c9-34c9-4623-bdb5-3f291f57a5be ro single
initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd0,3)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root

---

### Post by confused57 on 2007-12-13
This might be better:
```
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title WINDOWS VISTA (ALL USERS) HIGHLIGHT THIS AND HIT ENTER
root (hd0,0)
savedefault
makeactive
chainloader +1[/COLOR]

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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a8f235c9-34c9-4623-bdb5-3f291f57a5be ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=[COLOR="Red"](hd0,3)[/COLOR]

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##


title UBUNTU (7.10) (DO NOT ENTER - FOR RICHARD ONLY)
root (hd0,3)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=a8f235c9-34c9-4623-bdb5-3f291f57a5be ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title UBUNTU (7.10) (RECOVERY MODE - ONLY)
root (hd0,3)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=a8f235c9-34c9-4623-bdb5-3f291f57a5be ro single
initrd /boot/initrd.img-2.6.22-14-generic

#title Ubuntu 7.10, memtest86+
#root (hd0,3)
#kernel /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title Other operating systems:
#root
```If what you have works fine, then leave it as you have it.

---

### Post by techgeek40 on 2007-12-13
I'm going to print mine and your's out and look at them line by line (yes, I want to understand this very well).

If this all works out, I see no reason why I can't just get rid of EasyBCD and using the grub, allow it to either boot Vista/XP/Ubuntu

---

### Post by techgeek40 on 2007-12-13
> **confused57 said:**
> Great job getting it working, your perseverence paid off...You may have already done so, but the Vista entry needs to be above the ###BEGIN AUTOMAGIC KERNELS LIST, as described in this thread:
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk)
I have to keep the wife happy also, so the pc boots into Windows by default.

I assume you've permanently changed the grub entries in your menu.lst to (hd0,3)...you also need to change the line with #groot to (hd0,3):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
If you have a kernel update, update-grub is run, which would change your root back to what is listed in groot.

Added:  By the way, what changes did you make in your Vista grub entry in order to get Vista/XP to boot/

In the grub it points to the "EasyBCD" and then I have to highlight Vista or XP and then it will go in
SO basically I have to hit enter twice

---

### Post by confused57 on 2007-12-13
Just for the heck of it, try this entry to boot XP, using the hide commands for Vista:
```
title     Windows XP
hide      (hd0,0)
unhide    (hd0,4)
root      (hd0,4)
savedefault
makeactive
chainloader +1
```

If you're able to boot XP with this entry, you might be able to go into EasyBCD and remove the XP entry...then you possibly would eliminate the selection menu  when you boot to Vista?  You probably know if this might work or not, more so than I would.

---

### Post by techgeek40 on 2007-12-13
From the looks of this - it should work.
The EasyBCD actually is boot loader (drive partition) much like GRUB - 
Yes, it can be by-passed with GRUB - as long as the drive / partition are put in there


I know Microsoft recommends "older' version of the O/S to be installed first, but I have never agreed with that method, for the simple fact that most users will want the 'newest' first -

The Vista boot loader is actually a little better than XP's - so I want Vista first - and then XP

The sad part is that many will only be using the Vista Upgrade CD and not the full install. So it's best to install XP - then upgrade, then reinstall XP on a new partition - 

Sounds goofy - but it works better in my view.

---

### Post by confused57 on 2007-12-13
> **techgeek40 said:**
> From the looks of this - it should work.
The EasyBCD actually is boot loader (drive partition) much like GRUB - 
Yes, it can be by-passed with GRUB - as long as the drive / partition are put in there


I know Microsoft recommends "older' version of the O/S to be installed first, but I have never agreed with that method, for the simple fact that most users will want the 'newest' first -

The Vista boot loader is actually a little better than XP's - so I want Vista first - and then XP

The sad part is that many will only be using the Vista Upgrade CD and not the full install. So it's best to install XP - then upgrade, then reinstall XP on a new partition - 

Sounds goofy - but it works better in my view.
Thanks for the info...I've never used Vista, nor dual booted 2 different Windows versions, so I have to rely on what I've read or even better, someone else's experience.

---

### Post by techgeek40 on 2007-12-14
Well, it's official - I blew away my Vista and install Ubuntu

Now hopefully I can learn a lot

But my home computer (desktop) is now having problems
For some reasons my boot partitions are blowing out :<

---

