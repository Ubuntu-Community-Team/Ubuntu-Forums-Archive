---
title: "Windows 7 Dual Boot"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2010-07-25
Greetings.

I have been less than active lately (which may have been a relief to some of our gurus:) ) but that's because I am breaking in a new machine - a Dell Studio XPS with 6 cores.  (Not top of the line.)  As before, Windows must remain my primary OS.

I have already downloaded gparted live software and Ubuntu 10.4 but the posts I have seen so far are not encouraging; it looks like installing bootable Ubuntu (on a separate partition, of course) will damage Win-7's abolity to boot and will require the Win-7 disk (which I have) to repair the boot-loader.  I doubt that the Windows boot loader will be generous to Ubuntu by leaving the Ubuntu boot in place.  Most intimidating I have seen is the the thread started by *choosemyfate* a few days ago.  His biggest problem is that the grub2 boot script did not seem to automatically include the Windows boot.  This may be something he omitted when installing Ubuntu in the first place (which can be avoided) or some missing intelligence in the installation process.

Some may recall I had a miserable time of it when I installed 8.10 on my previous PC.  (I gave up then and took the chance again with 9.04, with success.) Can someone direct me to some fresh docs that address Windows 7 dual-booting with Ubuntu?

Thanks much.

---

### Post by Goolie on 2010-07-25
I installed Ubuntu 10.04 on my laptop with Win7 and it went off without a hitch.

Just smooth sailing.

---

### Post by drdos2006 on 2010-07-25
Install Windows 7 first, it tries to take control of MBR and all other harddrives. Ubuntu does not care where it is installed in order to boot. 

regards

---

### Post by efflandt on 2010-07-25
I have a new Dell Studio XPS 8100 w/i5 and 64-bit Win7.

For some reason I could not get 64-bit Lucid to boot from the far end of a 500 GB USB drive (that drive boots fine on 2 older laptops, but not on my old HP desktop from 2004).  But the XPS booted 64-bit Lucid fine from a 160 GB USB drive.

That is strange because when I installed Lucid to the 1 TB internal drive, I had no problems.  Although I shrunk Windows, just added one primary partition, put grub on that partition (instead of mbr), and used gparted to mark that as the boot partition.  I don't have any swap partition, but I do not really need it with 8 GB RAM as long as I do not want to hibernate (swap not needed for suspend).

NOTE:  Also save the output of **sudo fdisk -l** so you know how everything was originally. It is recommended to shrink the Win7 or Vista partition with its own tools (enter "computer management" in search field).  But first, create recovery discs (Dell no longer provides discs) and system backup (DVD's or USB formatted ntfs), so you have that if you mess up.

Everything worked out of the box for my XPS 8100 (including wireless), I just activated nvidia(195) driver for faster GT220 video.

---

### Post by Bluesan on 2010-07-25
> **rpaskudniak said:**
> Greetings.

I have been less than active lately (which may have been a relief to some of our gurus:) ) but that's because I am breaking in a new machine - a Dell Studio XPS with 6 cores.  (Not top of the line.)  As before, Windows must remain my primary OS.

I have already downloaded gparted live software and Ubuntu 10.4 but the posts I have seen so far are not encouraging; it looks like installing bootable Ubuntu (on a separate partition, of course) will damage Win-7's abolity to boot and will require the Win-7 disk (which I have) to repair the boot-loader.  I doubt that the Windows boot loader will be generous to Ubuntu by leaving the Ubuntu boot in place.  Most intimidating I have seen is the the thread started by *choosemyfate* a few days ago.  His biggest problem is that the grub2 boot script did not seem to automatically include the Windows boot.  This may be something he omitted when installing Ubuntu in the first place (which can be avoided) or some missing intelligence in the installation process.

Some may recall I had a miserable time of it when I installed 8.10 on my previous PC.  (I gave up then and took the chance again with 9.04, with success.) **Can someone direct me to some fresh docs that address Windows 7 dual-booting with Ubuntu?**

Thanks much.

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Sub101 on 2010-07-25
> **rpaskudniak said:**
> Greetings.
I doubt that the Windows boot loader will be generous to Ubuntu by leaving the Ubuntu boot in place.  Most intimidating I have seen is the the thread started by *choosemyfate* a few days ago.  His biggest problem is that the grub2 boot script did not seem to automatically include the Windows boot.  This may be something he omitted when installing Ubuntu in the first place (which can be avoided) or some missing intelligence in the installation process.


A lot of Dell pcs, such as my Alienware came with backup software. This software would rewrite the MBR everytime I shutdown Windows. The fix was to simply remove this software.

---

