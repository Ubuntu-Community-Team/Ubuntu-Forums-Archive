---
title: "Trying to Backup Files Before I Install 10.10"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by brantpadams on 2010-12-13
I have a pretty basic question that I can't find an answer to.

I currently have 10.04 and I want to do a fresh install of 10.10 via a disk install. When I upgraded to 10.04 I did it through the update manager which I later learned wasn't the best of ideas. After the initial upgrade I noticed a few flaws in my computers overall performance, most notably the startup was taking far longer than I have ever seen since I started using Ubuntu. I feel like the overall processing speed of my computer has fallen as well. 

I was told that doing a fresh install, i.e. wiping everything and then installing from a disk or flash drive is usually the best solution as it frees up space. I'd like to do this, but naturally I've accumulated a lot of files over the past year that I have no way of backing up. 

All I would like to know is if there is a way to back up all of my files without the use of an external hard drive. I've heard about backing them up on a separate partition and retrieving them when the installation is complete. 

Any help at all would be much appreciated.

---

### Post by dabl on 2010-12-13
> **brantpadams said:**
> 

 I've heard about backing them up on a separate partition and retrieving them when the installation is complete. 



Well, do you HAVE a separate partition?  Is it at least as large as the total size of all your data files?

You said you don't have an external hard drive, but if you have access to any working spare hard disk drive, you can make a temporary hookup with one of these:  [http://www.google.com/products/catalog?q=usb+to+sata+adapter+cable&um=1&ie=UTF-8&cid=9485045192101622072&ei=5NAGTbK6NoS0lQfIxfHGCQ&sa=X&oi=product_catalog_result&ct=result&resnum=5&ved=0CDgQ8wIwBA#](http://www.google.com/products/catalog?q=usb+to+sata+adapter+cable&um=1&ie=UTF-8&cid=9485045192101622072&ei=5NAGTbK6NoS0lQfIxfHGCQ&sa=X&oi=product_catalog_result&ct=result&resnum=5&ved=0CDgQ8wIwBA#)

That's just an example -- Google can show you lots of them.

---

### Post by brantpadams on 2010-12-14
I have a separate partition for Windows XP, but it only has about 25GB on it. The amount of space I need for a backup should be around 100GB or so and my laptop has 320GB of storage space. The XP partition really only needs maybe 10GB since I don't use it very often, but I don't really know how to change the amount of space I can partition. 

Can I create a new partition to back these files onto?

---

### Post by dabl on 2010-12-14
If you have unused space on your hard drive, either via a partition that is partially empty, or unallocated space, then you can use GParted to make a new partition, and (after mounting it) use that new partition to save your data.

Since all partitions need to be non-mounted when you work with GParted, I personally like to use a Parted Magic Live CD to do such things:  [http://sourceforge.net/projects/partedmagic/files/partedmagic/](http://sourceforge.net/projects/partedmagic/files/partedmagic/)

Note that you are allowed a maximum of 4 primary partitions.  You have already described 3 -- if you already have 4 and want to add another, then you must convert an existing partition to an extended type, and add logical partitions within it.

Also, do not shrink the Win XP partition without first booting Win XP, and running defrag.

This should get you started.  There are GParted tutorials scattered about the 'net, including here:  [http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by owiknowi on 2010-12-14
just a tip: if however possible backup your personal files to an external medium (CD/DVD/etc.)

if you just move them around on an internal hdd and that one goes permanently down, you loose everything.

shrinking an editing partitions can be a risk for existing os's.

and maybe already obvious to you: fat32 can only contain files up to 4GB (4096MB)

---

