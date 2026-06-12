---
title: "HowTo Mount an ext3 partition"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by seecoolguy on 2007-09-09
Let me just start w/ yes I am a nu b, but I have searched google to do many things on my fresh install of ubuntu fiesty fawn., I have been having a blast, i even installed vmware player to help me still get by on my needed windows only apps.

I've been searching for some time and have found lot's of help on how to mount window drives and even managed to mount my drives that were previously all NTFS (including an external USB buffalo drive).  However now I've formated my 120gb drive using gparted and all went well went to /etc/fstab and mounted that nicely over on /mnt/data next I have a 250 gb drive.  I seem to have had nothing but problems.  I tried using gparted and for some reason it did not handle creating the ext3 partition well on it.  so I found some terminal comands to learn how to do it via fdisk and the ext3 script.  now I run fdisk -l and I get this result

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706   83  Linux

I am assuming that I can mount my drive in the following way

edit /etc/fstab and add:
/dev/sda1 /mnt/video ext3 defaults 0 0

then 
sudo mount /dev/sda1 /mnt/video 

but I simply get this error:
mount: special device /dev/sda1 does not exist

any ideas?

---

### Post by merlinus on 2007-09-09
Did you create the mountpoint?

---

### Post by Pumalite on 2007-09-09
If you have dir /mnt/video already made, then, in terminal:
sudo mount -t ext3 /dev/sda1 /mnt/video
If not, then sudo mkdir /mnt/video

---

### Post by seecoolguy on 2007-09-10
i'm sorry I forgot to include that portion of info in my original post the location /mnt/video was created before I tried to mount (i've even rebooted a few times )

---

### Post by Pumalite on 2007-09-10
Then this should work:
sudo mount -t ext3 /dev/sda1 /mnt/video

---

### Post by seecoolguy on 2007-09-10
I tried the command sudo mount -t ext3 /dev/sda1 /mnt/video

I received the error:

mount: special device /dev/sda1 does not exist

---

### Post by merlinus on 2007-09-10
It is possible that it was not formatted correctly.  You might try gparted live cd to see if it recognizes the partition:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by seecoolguy on 2007-09-11
this is my process for using fdisk

sudo fdisk /dev/sda

The number of cylinders for this disk is set to 30515.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-30515, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-30515, default 30515): 
Using default value 30515

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

---

### Post by merlinus on 2007-09-11
So then what did you do to format it as ext3?

---

### Post by seecoolguy on 2007-09-11
After no success with ext3 I decided I would try my luck at Xfs but still to no avail.  I downloaded the iso for gparted live cd but it seemed to just get stuck and never get past a certain point while reading the hardware then it just dumped me back to the shell.  I had a copy of Acronis that I used to backup my original windows system (so I could do a universal restore to vmware). and decided I would clone the 120 to the 250 gb drive, but I found I could format a drive using the acronis tools.  What a cool trip!  I am now running ext3 after formating via Acronis the device name is /dev/sda5 not 1 like the gparted utility wanted or even the mkext3 script. :)

thanks to all who tried to help, i don't know what hung up my process if I was still mounted to the system as ntfs when I started and maybe that's why the partition via gparted was corrupted or what. but the end of the story is that it works now, and I am happy with my choice of ext3 though after re-searching the diff between xfs I may think about re-formatting and going the way of xfs at a later time since this is going to be my raw video drive :)

--
seecoolguy

---

### Post by southernman on 2007-09-11
As merlinus questions you... 

After you use fdisk to setup the partition you then have to format it to ext3 (or whatever filesystem you choose)

To do that as ext3, the command would look like
> 
sudo mke2fs -j /dev/sda1

Additionally you could change the [Reserved Space]("https://help.ubuntu.com/community/InstallingANewHardDrive#head-a11027f8a6eeff08eeed917910863d839612c631") to 1% from the standard 5% if you like.

---

### Post by seecoolguy on 2007-09-11
Thanks for the last link, I may choose to try a re-format using the linux tools one more time, at least I know how to get out of it if it bombs out on me again :)

---

### Post by southernman on 2007-09-11
NP coolguy. Didn't notice until after I posted you solved your problem. Glad I didn't edit it out now. ;)

Any trouble, just let us know.

---

