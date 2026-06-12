---
title: "New to Linux...Have Installation/Format Questions"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by mkukis on 2007-04-07
Hi all,
   I've recently been really interested in switching from XP pro to some distro of linux. I wanted to switch to Ubuntu due to all of its popularity. I downloaded the liveCD and booted it up and ran into some problems. When starting the CD, the graphics get a shearing effect. I'm pretty sure its just a lack of driver, due to my ATI Mobility FireGL V5000 (I'm trying to dual boot on my laptop, a HP nw8240). I'm pretty sure I can just fix that after its installed...

My next issue is with the partitioning process. As stated before i want to dual boot xp and ubuntu. I need to keep xp due to some programs I need for college. I partitioned 8 gb aside in FAT32 for the ubuntu install but then got confused when the installation asks for me to pick places for the "/" and "swap" and what not....I am unsure as what to do regarding these different things. Do i need to further split up that 8gb to allow for the various "/" ? Or can i just put the swap partition on one of my other partitions? I need some guidance on this part of the installation because i definitely do not want to lose any of my data. 
Thanks alot,
           Matt

---

### Post by solar george on 2007-04-07
/ is the called root, all files (and in linux everything is a file) are stored in directories in the root.
The swap space is used as extra ram-type memory (I believe that window$ calls it pagefiles).
You should create a partition for swap that is a similar size to your installed memory (RAM) the rest of the 8gb can be set to root (/).

---

### Post by Hendrixski on 2007-04-07
If I remember correctly there's an option that allows you to choose a percentage of your harddrive and Ubuntu will do all of thepartitioning for you.  The other option is the advanced install.... which is... advanced.  At least advanced in the sense that you have to know what UNIX based file systems look like.  So if you've ever used Solaris UNIX, Mac OS X,  IBM's AIX, or any form of Linux, you'll notice they're all very similar.  DOS unfortunately looks like nothing else because it re-invented the wheel.

---

### Post by Imsati on 2007-04-07
Taken from one of my posts a few months back. Some of it's probably relevant :-)

***
Ok...Unbuntu partitions...you'll want three of them: 1 Swap, 1 /Root, 1 /Home

Swap is (in simplest terms) to Linux what Virtual memory is to Windows. Make it double what your physicam RAM is (512 mb RAM = 1024 mb (1 GB) Swap partition)

Root is, again in simplest terms, the actual OS. By designating a separate partition for Root, you can delete/format/reinstall should you ever have a problem and not worry about losing all your personal files. Dont give it more that 15GB of HDD space, and that's looking a looooong way ahead; You'll probably need no more than 7 GB.

Home is going to be *your* partition for Ubuntu. Use this to store all your music, etc. files. Give this as much HDD space as you desire.

Those are your three basic Linux Partitions that you want, regardless of anything else.

I have a separate NTFS formatted XP drive, so I don't need to do this following step, but if you have only one HDD, take it into consideration...

If space allows, AFTER making sure the XP partition is the correct size and AFTER making sure the Ubuntu partitions (all three of them) have the correct size, you can make another FAT32 partition so both Windows and Ubuntu can read with the greatest ease.

But...PLEASE BACKUP important files before doing so...some folks learn that the hard way...and it's not pretty

~Jay

---

