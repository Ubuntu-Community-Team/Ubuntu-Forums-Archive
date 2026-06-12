---
title: "&quot;Select and Install Software&quot; GLOBAL Failure"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by PelPix on 2011-10-16
For some reason, I can't install Ubuntu.  It fails at "Select and Install Software" *every single time*.
Now, normally I'd just check the md5 sum and reburn the disk a few times at 1X, but the problem isn't data corruption!  Every single distro that is based on Debian or uses its installer will not install on my system.  Wheezy, Squeeze, Sid, Hannah Montana Linux, Ubuntu, Xubuntu, Kubuntu, what have you.  They won't install!

Suggestions?

---

### Post by 23dornot23d on 2011-10-16
What system do you have

how much disk space

how much ram

what graphics card

desktop or laptop .... ?

---

### Post by PelPix on 2011-10-16
> **23dornot23d said:**
> What system do you have

how much disk space

how much ram

what graphics card

desktop or laptop .... ?

64GB in the space I opened up for Linux.  16GB DDR3 RAM.  Radeon HD6850, Desktop.  Built.

---

### Post by 23dornot23d on 2011-10-17
I would be looking at the hard drive you use ..... and if its being allowed to write to it ....

Something tells me that if it fails on every distro ..... its either not picking up the hard drive properly
or
Its some strange format ..... on the hard drive ....

or you already have 4 primary partitions set up ..... and one need to be extended ..... so

Create a extended partition and put in it the following .......
  
ext4 using gparted from a LiveCD ....... and try it again ......



If it formats ok ...... then thats a start ....

and post a screenshot of the gparted screen please .......

ideally you need 
/ 
/home 
swap space 

but / which is root (20 Gig plus) and swap (4Gig-8Gig) will do to start with .......... just to test it

Hope we can sort this out ......

---

### Post by PelPix on 2011-10-17
I've been using debian-based linux distros since sarge.  I am doing everything like I have always been doing it.

I don't think it's having any trouble finding the drive.  Installing the Base System goes absolutely swimmingly.  It's only Select and Install Software that messes up.  You are assuming that I am having a problem formatting the disk.  I'm not!  Everything formats perfectly every single time!

I have tried the following partitioning arrangements (All of the above worked on my old computer):
ext2 /boot
ext4 /

ext2 /boot
btrfs /

ext2 /boot
ext4 /
ReiserFS /home

And to bug hunt:

ext2 /

Usually only /boot is a primary partition.  The rest are logical.  However, to attempt to fix this problem, I have tried every single other possible combination of logical and primary partitions.  Live CDs install absolutely fine and work 100% perfectly with no bugs.  It's only manual installation that presents any sort of problem.

---

### Post by PelPix on 2011-10-22
?????
It does it in virtual machines too!

---

