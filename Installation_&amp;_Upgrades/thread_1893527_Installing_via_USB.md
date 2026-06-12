---
title: "Installing via USB"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by Tim Legg on 2011-12-10
I have a netbook with no CD-ROM.  It has Windows which has never been booted (new from factory).  I have dd'd the hard disk to make a backup already.

I want to install Ubuntu 10.04 on it's own partition alongside windows.

When you have a CD-ROM, the install tool does a beautiful job of installing and modifying the partitions.

The problem lies is two places:

*  Ubuntu.com, unlike many, many other distros, does not provide a USB install image, only ISO.  I won't address this any further here because I don't want to express my true feelings and opinions on this in this thread.

*  Since I have used Ubuntu, the Make Startup Disk tool has never worked even once for me.  It either crashes, hangs, or, in the case of this morning, just sits there with the "Make Startup Disk" ghosted out for no apparent reason, despite a 2GB USB drive and 10.04-3 i386 image being selected.  The usefulness/robustness/reliability of this tool is also something that I can go on about in relation to the first bullet point above.  That too is for a different thread because I have very strong words to say about these two points.

-----

In the past, I did a workaround.  I create a 8GB zero file and run qemu to install Ubuntu on it.  Then I dd the image file to the hard disk of the netbook.  Boot the netbook with a partition management tool and resize the partition.  Takes a long time, but it works and I am able to install Ubuntu on a netbook.

But the difference is that this time, I need to install this next to windows.  I am considering these steps:

1.  Use dd to extract the partition from 8GB image file.
2.  Boot netbook with partitioning tool and resize the partitions.  
3.  book netbook with debian live USB image to run fdisk, create swap and ext3 root partition sized to the size of the file extracted in step 1.
4.  Calculate the offset of the partition on the hard disk and dd the partition image there.
5.  Resize partition with the partitioning tool.
6.  Configure grub.
7.  Pray that what man hath created may no error run us under.
8.  Test. Restore image, tweak plan, restart procedure.


Does anybody see any problems with this procedure?  It will take several hours to complete.  I am no expert in how ext2/3 filesystems work, but if there is any drive geometry attached to the data structures of the filesystem, I am in trouble.  Does anybody see any issue with this?

Tim Legg

---

### Post by MG&amp;TL on 2011-12-10
Two things leap out right away:

1. Make an image, then make a copy of it to install.

2. Use a different tool. I use unetbootin and it works fine. Also, I find it works best if you make a windows filesystem on the stick, then make a partition on the stick. IDK why, but it seems to work better like this.

---

### Post by pickelhaupt on 2011-12-10
Creating a live USB from Windows is very easy using e.g. LiLi [http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download) 

The just insert the stick in the netbook, start the computer and hold down F11 during boot in order to get to the boot menu. Then choose USB as boot source and hit ENTER and Ubuntu will start. Choose "try ubuntu" if you want to make partitions (using gparted) prior to the dual boot setup.

/K

---

### Post by Tim Legg on 2011-12-10
This doesn't work either...

> **pickelhaupt said:**
> Creating a live USB from Windows is very easy using e.g. LiLi [http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download) 

The just insert the stick in the netbook, start the computer and hold down F11 during boot in order to get to the boot menu. Then choose USB as boot source and hit ENTER and Ubuntu will start. Choose "try ubuntu" if you want to make partitions (using gparted) prior to the dual boot setup.

/K

I took my freshly formatted 2GB USB drive and a 10.04-3 AMD64 ISO CD.  I ran the tool.  It completed the steps fairly quickly.  Booting from the USB drive doesn't work.

SYSLINUX 3.86 2010-04-01 EBIOS Copyright (c) 1994-2010 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot:

I did the same with the 10.04-3 i386 ISO.  It took substantially longer to perform, but behaves identically when booting from USB

It does the same in a virtual machine too.

---

### Post by Lars Noodén on 2011-12-10
> **Tim Legg said:**
> I have a netbook with no CD-ROM.  It has Windows which has never been booted (new from factory).  I have dd'd the hard disk to make a backup already.

If it's not been booted you could still try for a [windows refund](http://www.google.com/search?q=windows+refund).

---

### Post by Tim Legg on 2012-01-05
The windows and linux based USB installer creation tools were provided and neither one worked (Ubuntu needs to be more aggressive in making the installers more accessible.  Really guys, are you hurting that badly for disk space? At least a torrent file?)

I found a solution/workaround for this problem.

You need two fairly large USB pen drives and a host computer running Ubuntu.


[LIST]
[*]I created an 8Gb null file using dd as a hard disk image
[*]Make sure your USB disk can hold a file this size.  You might be able to get away with something between 4-8GB.
[*]I launched qemu with the CD image to install linux onto this image.
[*]  - Life is easier when you set swap to be the first partition.
[*]I copy this image file to a USB storage device.
[*]I downloaded a copy of debian live usb-hdd from [http://live.debian.net](http://live.debian.net) and dd'd the image to a second USB pen drive (like I should be doing with an installer)
[*]Boot netbook from pen drive
[*]I used dd to copy this 8GB file to the hard disk.
[*]I resized the partition to occupy the entire hard disk (using fdisk and resize2fs)
[/LIST]

If you use Debian standard USB image, you can get away with a 512MB USB drive.  For the other drive, 8GB is big enough.  If your image doesn't fit on your drive, try using gzip to compress it; it can decompress using gzip -c > /dev/sda

---

