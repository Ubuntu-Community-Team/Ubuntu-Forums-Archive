---
title: "Installs OK but does not boot..."
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by xcliber on 2007-04-26
First off, I have 2 hard drives.
one is a sata device and the other is IDE
I have the sata drive separated into 2 partitions.
-system info from within Windows Vista says:

Description	Disk drive
Manufacturer	(Standard disk drives)
Model	IC35L060AVER07-0 ATA Device
Bytes/Sector	512
Media Loaded	Yes
Media Type	Fixed hard disk
Partitions	2
SCSI Bus	0
SCSI Logical Unit	0
SCSI Port	1
SCSI Target ID	0
Sectors/Track	63
Size	55.87 GB (59,995,192,320 bytes)
Total Cylinders	7,294
Total Sectors	117,178,110
Total Tracks	1,859,970
Tracks/Cylinder	255
Partition	Disk #0, Partition #0
Partition Size	53.09 GB (57,001,158,144 bytes)
Partition Starting Offset	32,256 bytes
Partition	Disk #0, Partition #1
Partition Size	2.79 GB (2,994,001,920 bytes)
Partition Starting Offset	57,001,190,400 bytes
	
Description	Disk drive
Manufacturer	(Standard disk drives)
Model	NVIDIA  JBOD     232.88G
Bytes/Sector	512
Media Loaded	Yes
Media Type	Fixed hard disk
Partitions	2
SCSI Bus	0
SCSI Logical Unit	0
SCSI Port	0
SCSI Target ID	1
Sectors/Track	63
Size	232.88 GB (250,056,737,280 bytes)
Total Cylinders	30,401
Total Sectors	488,392,065
Total Tracks	7,752,255
Tracks/Cylinder	255
Partition	Disk #1, Partition #0
Partition Size	130.46 GB (140,083,462,144 bytes)
Partition Starting Offset	1,048,576 bytes
Partition	Disk #1, Partition #1
Partition Size	102.42 GB (109,973,602,304 bytes)
Partition Starting Offset	140,084,510,720 bytes

I had Vista installed first on Disk #1, Partition #0
and I have just installed Ubuntu 7.somthin (latest release that im aware of) on this drive:

Partition	Disk #0, Partition #0
Partition Size	53.09 GB (57,001,158,144 bytes)
Partition Starting Offset	32,256 bytes
Partition	Disk #0, Partition #1
Partition Size	2.79 GB (2,994,001,920 bytes)
Partition Starting Offset	57,001,190,400 bytes

Everything went smoothly until I went to actually BOOT Ubuntu...
Grub appears and lists my boot options:
ubuntu (I don't know the rest of this offhand but i would think its standard)
ubuntu safeboot (same with this one)
kernel somethinorother
memtest
other operating systems:
Windows Vista

So i choose the first one which is the default...
It appears to load at first but then, right before it reaches the Ubuntu logo, the system restarts itself...
so after a few tries i tried the recovery mode thing but was left clueless when it asked for input  as I AM NEW TO LINUX.

The vista option starts up the vista bootloader and from there has no trouble booting to windows.

Someone PLZ help...

---

### Post by Herman on 2007-04-27
Hello xcliber,
If you're not afraid of trying to use grub's command line (typing your own commands and pressing 'enter'), you can press your 'c' key from your grub menu and enter grub's command line mode. From there you can use grub to investigate what's going on and try to boot Ubuntu manually. That will help to find and work around 99% of grub problems. Take notes of what commands you make up because the same commands that can boot Ubuntu from the command line can be used to fix grub's menu.lst file to make Ubuntu boot automatically from now on. Here is a link that should help you, [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

If you don't think you can do it that way, there is an easier way. You can download [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and burn that to a CD and try to boot Ubuntu with that. The most reliable way to boot Ubuntu with Super Grub Disk would be to boot Super Grub Disk and then go 'English Super Grub Disk' (menu)-->'Gnu/Linux'-->'Boot Gnu/Linux Directly'. You will see what I mean when you try it. 'Boot Gnu/Linux Directly bypasses most of the possible trouble spots you would be likely to have when trying to boot Ubuntu. That should boot it. Once it is booted you will still probably want to fix it for next time, probably by editing your menu.lst file. It will be easier to test and obtain information needed for doing that when you have Ubuntu booted. 

Either of those suggestions should help you, (I hope), good luck,
Regards, Herman :)

---

### Post by GaTk on 2007-04-27
Hi guys,

Herman's suggestion to get SGD caught my eye ... I have downloaded both the diskette and USB versions to try.  This gives you the capability and flexibility to handle the GRUB mess created by MOST distros.  At this particular time I have WINXP Pro, WIN98, and 5 Linux distros scattered across 3 IDE drives.  Of course, the WIN stuff is on my C (hda) drive with a dual boot loader in the MBR of  /dev/hda.  I am a distro junkie and have loaded and run most of the major distros in my quest for a distro that wiil play video streams from CNN... but that's another story!!!   I haven't kept score, but most of the distros stick with mickeytsofts philosophy that EVERBODY installs on the first hard drive and if you're bold enough to install somewhere else it is likely your newly installed distro will not boot -- and worse yet, she will trash the MBR on your first drive.  I currently use a diskette to boot any of my distros that are described in a grub.conf file that resides on hdc1.  This is the boot partition of my Fedora FC6 partition and after installing a new distro, I use NANO to manually update the grub.conf file with the information necessary to boot the new distro.  Stick with it... and spend sometime understanding how GRUB works  There are lots of GRUB howtos available on the Inet.. I learned a bunch from one called Grub From the Ground Up by Steve Litt.. 

One other point, most distros now come in LIVE-CD form and are a great way to become familiar with a distro.  If you're about to try a new one, scan the forums for that distro and read about the successes and failures. 

Good luck

Ted in Atlanta

---

### Post by Herman on 2007-04-27
Here is the link to Steve Litt's main page ' [Grub Grotto]("http://www.troubleshooters.com/linux/grub/index.htm") '.  :)
Steve Litt's 'Grub From the Ground Up' is an excellent Grub tutorial, I like that one too! There are two more Grub tutorials by Steve Litt there too, 'Grub Special Boots and Other Tips', and 'Making a Dedicated Grub Partition'.

I agree with GaTk, I can't imagine how anyone could still have trouble with Grub if they take a little time to read up on it and learn how to use Grub. 
Most people don't even need to learn how to use Grub though, we really don't have a large percentage of booting problems here when you consider the numbers of new people installing each day. Most people don't need to learn anything about Grub. Currently around 800 to 900 people per day are joining Ubuntu Web Forums, and if that's any indication of the numbers of Ubuntu installations going on, I would think that the number of grub questions is relatively small in proportion.
[Super Grub Disk]("http://supergrub.forjamari.linex.org/") is a great help in most cases, probably there are some people who don't even need to post a question, but can quietly solve their own problem with Super Grub Disk without any help.

I don't know what you mean by 'trash the MBR on your first drive' though, GaTk. :)
It's almost always a good idea to install Grub to MBR on the first hard disk and replace the IPL for the Windows bootloader there. Here is a link to a really good tutorial on how to multi boot more than one Windows operating system, [    Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") , by Dan Goodall.
When you have read and understood that tutorial, you will understand what I mean, it is better to use a 'third party boot manager' (that is: Grub), in MBR than to dual boot the Microsoft way. You can use Grub's 'hide' command to set up a Windows dual or multi boot, which is a much smarter way to do it. :wink:
Anyhow, each to their own beliefs and opinions I guess, think about it though.

Regards,  Herman  :)

---

