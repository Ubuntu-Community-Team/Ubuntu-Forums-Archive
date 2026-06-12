---
title: "Please Update information on 64 bit vs 32 bit"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by 8301 on 2010-02-24
Iam setting up a HTPC system most advanced thing is 1080p playback with XBMC, Surf, Flash sites, Home server.

Hardware is
CPU AMD 4850e 2.5 ghz dual core
GPU msi Nvidia 210n
RAM 4 gig
Memory 5 terrabyte
sound realtek HD

I have searched around on google and find no new information on the pro and cons for the keramic koala 9.10 64 bit system. 

Is everything working? Or am I driving thou a wall?

---

### Post by dabl on 2010-02-24
True 64-bit issues are so infrequent they shut down the sub-forum 3 months ago. That should give you a hint .... :D

Seriously, I don't see anything on your list of hardware that is going to be any more or less difficult to get working with a 64-bit OS than with a 32-bit OS.  (Good news/bad news).

---

### Post by Sef on 2010-02-24
Download the 64-bit Live CD and find out if there are any problems.   Any problems with the Live CD will almost always show up upon install.

---

### Post by Jeff Anthony on 2010-02-24
I'm using Karmic 64-bit, it's not overly buggy and I imagine you'll have no issues setting up your project using it. The largest reason to move to 64-bit is to be able to use more than 4GB RAM; where I have 8 I needed it. If you ever plan on upgrading the RAM 64-bit is the way to go

---

### Post by 8301 on 2010-02-24
The most thing I want to is stability 
So Ive got no problems to run 32 bit

Next question I have is for the system is I have used Ubuntu for 3 years now and tired of all the programs I dont use xsane, f-spot (i use gpicview), Totem (I want VLC) and so on. 

Should I try a different dist ex Xubuntu or mythtv or even server edition and install GUI to get a basic desktop.

The problem is that I dont have the know how about how a linux system builds looks like and how they work together. Iam thinking like a Windows system is build and try to compare that thought to ubuntu.

For example where is the equilient to windows program folder in ubuntu? Is there one

---

### Post by Sef on 2010-02-24
> The most thing I want to is stability 

There is no difference in stability between 64 and 32 bit systems.

---

### Post by wojox on 2010-02-24
I've run 32 and 64 bit Karmic on an AMD64 and not really seen that big a difference as far as speed or anything. I'm using 64 bit Karmic now cause I figure hey I got mine as well use it. No problems here.

I  noticed you have 4Gb of RAM so I'd go 64 bit.

---

### Post by ghostborg on 2010-02-24
64bit for the 4 gig. 32 generally only sees 3.37 gig.
Unless your video is shared memory space, that would subtract from the 4gig.

Netflix streaming does not work with Linux as far as I know.
Kinda sucks anyway.

---

### Post by oldfred on 2010-02-24
Where things are in Linux.

Explanation of file structure

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Since you can install in 10-20GB install both. I would not recommend sharing /home, but you can share all your data.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by Jeff Anthony on 2010-02-25
also try

```
sudo apt-get install vlc
```

---

