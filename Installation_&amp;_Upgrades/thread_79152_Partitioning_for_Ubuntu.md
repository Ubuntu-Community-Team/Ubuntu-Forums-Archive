---
title: "Partitioning for Ubuntu"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by iceman23 on 2005-10-19
Can the Ubuntu Installer CD partition for a dual-boot system from the installer? I'd like to do a dual boot and not lose my current windows system and files. Thanks for the help :D

---

### Post by wjp.reg on 2005-10-19
Partition it in terms of freeing up space? no, not unless you want to wipe out windows.

if you free up some space by shrinking windows first  then ubuntu will use that free space to creat its own partitions for root and swap

---

### Post by iceman23 on 2005-10-19
I have free space on the harddrive, I just want to use it as a new partition for Ubuntu, but if possible not delete the existing files on the first partition.

---

### Post by matthew on 2005-10-19
[quote=iceman23]I have free space on the harddrive, I just want to use it as a new partition for Ubuntu, but if possible not delete the existing files on the first partition.[/quote]
Then the answer is yes, most definitely. The Ubuntu installer can find the existing, unused free space and install itself there without harming your Windows installation. It will even set it up so you can choose which OS to boot into at startup.

---

### Post by iceman23 on 2005-10-19
Awesome! Will it be fairly straightforward or should I know some things before I take the plunge?

---

### Post by wjp.reg on 2005-10-19
[QUOTE=iceman23]Awesome! Will it be fairly straightforward or should I know some things before I take the plunge?[/QUOTE]

Keep pressing the <ok> button  ;)

---

### Post by r3m0t on 2005-10-19
wjp.reg appears to be incorrect. You can resize NTFS partitions (i.e. Windows ones) from within the installer ([source]("https://wiki.ubuntu.com//HoaryGoals")).

Resizing FAT32 partitions (i.e. Windows 95/98/ME ones, and possibly later ones) is certainly possible.

Be sure to defragment the partition first ([source]("https://wiki.ubuntu.com/WindowsDualBootHowTo")).  That's Start > (All) Applications > Accessories > System Tools > Disk Defragmenter.

This increases the chances of the partition being resized successfully and therefore gives you more usable time with your computer.

Of course, if you are defragmenting C: then I would suggest browsing with the cache off in Firefox and not writing to the disk much in any other way.:p

*Edit*: with all my sourcing I appear to have been relatively slow! Whoops/never mind!:KS

---

### Post by iceman23 on 2005-10-19
Well, I went into the installer to check out the partitioning part and it was there and easy to use. I just want to confirm my steps before going ahead with it.

I go to manually partition, and then resize my 120GB partition with windows, leaving free space to install linux. Then I select the free space and partition it. Does this look right? It seems to me that resizing the first partition would delete my files as it doesn't shoe what space is used and unused. Thanks for the help again guys!

---

### Post by dhatfield on 2005-11-13
I have decided to take the plunge and go Ubuntu.  I am amazed at the progress that has been made in terms of useability and hardware support by the Linux community in the last couple of years (I have aborted various attempts to migrate in the past due to technical and interface irritations).  Amazing work.

That said, I apologise that my first post is a whinge, but I have a few comments.
1.  Can we please have a screen in the installer / partitioner that says "If you are planning to dual-boot, quit this install, boot into Windows and DEFRAG FIRST"
2.  Can you please put some kind of message on the screen while the re-partitioning is in progress.  A blank blue screen and a thrashing hard-drive screams BSOD to a Windows user.  It took nerves of steel to wait out the (15-20 min) delay while Ubuntu figured out that it could create a new partition on the drive.  When you are doing hectic, hard-core stuff to my drive, please make re-assuring noises about it.
3.  The partitioning is a little glitchy in other ways.  On my 160GB drive (fragmented), guided partitioning said I had to make a partition of 97GB (57%) minimum, told me that a partition of 'max' and 50% could not be made, accepted a partition specified at 120GB (the default it gave me), and then made a partition of 34GB size and a 1.4 GB swap.  Very impressive that it took a whole lot of garbage in and made a useable partition out of it, but some correlation between specified size, final size and error messages would be optimal.  

That said, I am immensely impressed that this first thorny hurdle has been passed without any wailing or gnashing of teeth, just a little sweating.  Thanks for making my Sunday evening a good one.

---

### Post by aysiu on 2005-11-13
To dhatfield:

I'd highly suggest checking out [Got ideas for Dapper? Let the developers know! Posting here is not enough!](http://www.ubuntuforums.org/showthread.php?t=75000&highlight=dapper). Developers do not read these forums. We're all volunteers and fellow users here. Suggestions posted to the forums fall on deaf ears... or at least ears that aren't in charge of making changes.

To iceman23:

I understand that you don't want to lose your data, but please, please, please back up your work. Will the Ubuntu installation *probably* work flawlessly? Sure. Is there a small chance it may not? Sure. That's why you should back up. It's like driving without a seat belt, riding a bike without a helmet, weight-lifting without a spotter... repartitioning and installing an OS without backing up your work.

Borrow an external hard drive. Burn 100 CDs. Do what you have to do, but **please back up your work**.

That said, [this tutorial](http://users.bigpond.net.au/hermanzone/) is the best one I've ever seen for setting up a dual boot with Ubuntu and Windows.

---

