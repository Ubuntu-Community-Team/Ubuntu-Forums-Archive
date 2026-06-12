---
title: "Dual boot install order on a fresh disk"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by lominare on 2006-08-18
Hello,
I have parts on order for a new box that I plan to build in the near future.  I've used linux off and on for years now, but my wife  and some work-related software won't allow me to ditch windows altogether just yet, so my plan is to dual-boot Windows 2000 and Ubuntu (preferably with xgl, but that's another post :D )

I'm using the following (tell me if you need more specs):
AMD 64 X2 3800+ AM2 processor
Western Digital 250GB SATA2 hard drive

I would like to have something like a 25GB partition for each of Ubuntu and Windows, and then use the rest of the hard drive as a data partition that can be accessed by both operating systems.  It will have music, video, pictures, etc.

My questions are:
In what order should I install things?  In the past my drives have had Windows on them already when I've installed linux.  Should I install windows first and then shrink the partition, or should I partition first?  Will it be harder to install the boot loader one way or the other?  Does it matter?

Second, what filesystem should I use for the 'data' partition so as to have maximum compatibility with both systems?

Thanks for any help you can offer!

---

### Post by meng on 2006-08-18
My suggestion is install windows first, linux second.
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by JerMe on 2006-08-18
Windows first.  Unless you like torturing yourself. ;)  I'd give Windows 15-20GB if you're going to install large things like multiple games, otherwise 10-15GB is ok.

For Ubuntu, I'd give 15-25GB if you're going to be running Windows XP "virtually" (as in another window while you're in Ubuntu.)

As for your 'data' partition, you have a choice.  You can format it to be FAT32 (VFAT) or you can use Ext3.  FAT32 can be read natively by both operating systems but is limited by the 4GB max filesize, and speed to some degree.  Ext3 can be read natively by Linux, and can be read by Windows with a driver from [http://www.fs-driver.org](http://www.fs-driver.org).  IMHO, Ext3 is the way to go.

---

### Post by lominare on 2006-08-18
Thanks for the advice and links!  I wasn't aware of fs-drive, but it looks very cool.

---

