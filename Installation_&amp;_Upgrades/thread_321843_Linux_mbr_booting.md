---
title: "Linux mbr booting"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by srgess on 2006-12-19
Due to grub Error 22 i got tired of grub and want to boot linux with mbr but im not sure how to do it, if you did it with mbr can you help me i dont know what to put into the boot mbr setup, there picture of my hard drive setup.

Hard Drive setup:
[http://img182.imageshack.us/img182/3...rtitionqx8.jpg](http://img182.imageshack.us/img182/3...rtitionqx8.jpg)

Disk 0 and 1 are IDE drive
Disk 2 is SATA Drive

There my question in this picture of boot loader text:
[http://img263.imageshack.us/img263/6506/bootpp6.jpg](http://img263.imageshack.us/img263/6506/bootpp6.jpg)

Or is there any boot loader i can install with windows or booting on a cd because i dont have floppy and i cant get into linux but its freshly installed.

---

### Post by bulldog on 2006-12-19
22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

A bit confusing,how do you try to boot Ubuntu now?

When you installed ubuntu you probably installed GRUB somewhere in the MBR of one of your disks.
The art is to find where you installed it.
Mostly it install on hd0,your first boot device,but if you have used the alternate install cd,you had an option to install it on a other disk.
Don't go messing with your boot.ini if you don't know what you're doing.

---

### Post by Herman on 2006-12-20
Hello srgess,
If you have trouble booting with Grub and you don't like configuring bootloaders manually, there is an easier boot manager you can use which is 'Graphical', and easier for most people to configure. It is called [GAG Boot Manager]("http://gag.sourceforge.net/")
 and here is a web page to explain all about it, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")
It is easier to boot Windows with.

To boot Ubuntu with it, you need to install either Grub or Lilo bootloaders to the first sector of the Ubuntu partition.  That is an easy job. 
One way is to use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and go 'English Super Grub Disk'-->'Advanced'-->'Grub'-->'Restore Grub in a Partition'-->'Manual Restore GRUB in a partition', then tell Super Grub Disk what hard disk Ubuntu is on and what partition Ubuntu is in.
Other ways to install Grub or Lilo to the Ubuntu partition are also explained on that web page I already linked you to.

GAG Boot Manager can be installed to MBR, or used on a floppy disk or from a CD. It works best from MBR or floppy disk, but will also work from a CD. You can try it out from CD, then if you like it then install to MBR when you are ready.
GAG Boot Manger is very good for anybody, and I believe it is very reliable. GAG would be especially good for people who like to unplug hard disks and plug in different ones and delete and install new operating systems very often.

I wish you good luck with GAG Boot Manager if you decide to try it and I hope it solves your problems,  

Regards, Herman  :D

---

### Post by wavesound on 2007-01-24
> **Herman said:**
> Hello srgess,
If you have trouble booting with Grub and you don't like configuring bootloaders manually, there is an easier boot manager you can use which is 'Graphical', and easier for most people to configure. It is called [GAG Boot Manager]("http://gag.sourceforge.net/")
 and here is a web page to explain all about it, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")
It is easier to boot Windows with.

To boot Ubuntu with it, you need to install either Grub or Lilo bootloaders to the first sector of the Ubuntu partition.  That is an easy job. 
One way is to use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and go 'English Super Grub Disk'-->'Advanced'-->'Grub'-->'Restore Grub in a Partition'-->'Manual Restore GRUB in a partition', then tell Super Grub Disk what hard disk Ubuntu is on and what partition Ubuntu is in.
Other ways to install Grub or Lilo to the Ubuntu partition are also explained on that web page I already linked you to.

GAG Boot Manager can be installed to MBR, or used on a floppy disk or from a CD. It works best from MBR or floppy disk, but will also work from a CD. You can try it out from CD, then if you like it then install to MBR when you are ready.
GAG Boot Manger is very good for anybody, and I believe it is very reliable. GAG would be especially good for people who like to unplug hard disks and plug in different ones and delete and install new operating systems very often.

I wish you good luck with GAG Boot Manager if you decide to try it and I hope it solves your problems,  

Regards, Herman  :D

Hi After losing a HD and installing a new SATA I needed to use this.
I can now get windows running but it doesn't seem to find my linux partitions
at all.
I have:
hdc Ubuntu dapper
sda should be edgy ( But I cant boot it!)


I have looked at this help site:

[www.users.bigpond.net.au/hermanzone/p12.htm](www.users.bigpond.net.au/hermanzone/p12.htm)

I seem to get the partition across 3 pages and have to select a number 1 to 3 to get them.

Also I have to reset Gag each time I boot, even though I have it on the mbr, it seems to forget.  :( 


Just a few points and wonder if you know a way round this.
Cheers
Bob  :D

---

### Post by orb9220 on 2007-01-24
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

