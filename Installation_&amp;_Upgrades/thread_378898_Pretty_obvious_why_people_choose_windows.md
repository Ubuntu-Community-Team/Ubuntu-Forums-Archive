---
title: "Pretty obvious why people choose windows"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by crushdance on 2007-03-07
I have a lot of experience with windows machines and have read a lot about linux and OSX. 

I decided to try this out yesterday and realized that Ubuntu is the best release for home users. I burned the CD and used Partition Magic to set up an ext3 file and a swap file on my other hard drive.

Lo and behold apparently the image had an error on it and couldn't finish installing. I couldn't load back into windows either as it asked for the Linux CD. And I didn't want to tamper with anything in fear of losing bootability my two XP installations on the drives.

So I went to university today and after class burned two copies again to try and make this work. Now I'm at home and trying to install this *@#$%*&^" thing, btw I'm using the LIVE cd. I started the install and tried to instlal but everytime the installer says that the "root system" isn't selected. And I already made a partition for it beforehand which is 70Gb and ext3. Plus a 500mb Swap on another drive. I selected the "/" and same stupid message.

So I tried the automatic install and it asks me to select a size of the partition and I set it to 10GB so I could just add the 70Gb partition to it after using Partition Magic. I flick "forward" and nothing, the forward button grays out and the installer just sits there.

This is freaking rediculous. I'm running off the live CD and anything worhtwhile causes it to freeze and I have to reset and wait another 10 minutes for the live cd to load all over again.

Can someone tell me what I'm doing wrong or what Linux is doing wrong? Because I just want my windows installations back. This was I think a bad idea. It should have been painfully obvious why Linux isn't the majority even though Microsoft can be a pain at least their products work, especially during installs. With the way things are I'd be better off getting a mac mini to experience a different OS. Ubuntu is nice, but if you can't use it then whats the point?

[sorry for the thread title, I'm just really frustrated]

---

### Post by Sef on 2007-03-07
1) Do NOT use Partition Magic.   There have been problems with getting it and Linux to work together.  If you don't want to use the partitioner on Ubuntu (which is an older version of GParted), use the latest version of [GParted]("http://gparted.sourceforge.net/") itself.

2) Did you md5sum the download?  If not, the download could be bad.

3) Did you burn the iso at 4x or less?  Burning it at a higher speed can corrupt the burn.

---

### Post by taurus on 2007-03-07
4.  Use the alternate CD since it works better.

[http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-alternate-i386.iso](http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-alternate-i386.iso)

---

### Post by crushdance on 2007-03-07
Yes I checked the download and its fine.

I downloaded the one yesterday that installs from the CD the non live one. Is that the "alternate" one?

I tried installing again using the live cd and its not doing anything once again on step 5

I have a CD:RW that I burned the live cd on. Can I erase it using the live OS and burn it using the live OS? If so how?

---

### Post by crushdance on 2007-03-07
omg is there anyway I can install this thing via the bootscreen via a command without resorting to the dumb live installer?

I tried downloading the alternate one and the live os crashes at like 25% or so.

Why did I even do this...

---

### Post by Netspeed on 2007-03-08
I had the same problem as you. Try the alternate version and burn it as slow as possible.

---

### Post by Jonne on 2007-03-08
I've had problems with Partition Magic before (that was when I didn't know you could use a Linux Live CD and QTParted/Gparted to get the job done better and faster).

Partition Magic is a piece of crap, just use the partition editor on the Ubuntu LiveCD (System>Administration>GNOME Partition editor).

Anyway, what are your computer's specs? And have you tried checking if your memory is ok (the liveCD can do that, it does take a while)? I don't think I've ever experienced a LiveCD hang, personally.

---

### Post by floke on 2007-03-08
Also, what version of Ubuntu are you trying to install, Dapper, Edgy, or Feisty?
And before blowing off about how poor Linux is, stop and think: you didn't even know what the 'alternative install' was, so it's clear that you didn't exactly do a whole lot of reading on the issue before jumping in. I only say this since people will be more inclined to help out if you don't start chucking insults around. Still, I know you're frustrated, and I know that Linux can turn normal people into raging torments of angryness.

If you're trying to install Feisty then:

(a) you probably shouldn't, since its not stable yet
(b) It would explain your problem with the root partition, since it has a strange instal process.

How you getting on with the alternate install?

---

### Post by Netspeed on 2007-03-08
I can understand his frustration because Ubuntu and its derivatives have been written to cover a multitude of different computers which makes it difficult to find the correct install method. 

I'm still having problems with my alterrnate CD install. The system is painfully slow and I'm trying to figure out why. I can't copy/paste the terminal lines because I'm emailing from a different computer. I have 2gb of RAM and a Pentium d 805 if it matters...

---

### Post by nero_86 on 2007-03-08
Installing Edgy I had the same problem but selecting the root partition for last after partitioning everything worked fine.
Probably there is a little bug...

---

### Post by Cobikegeek on 2007-03-08
Installing windows seems easier because it doesn't make any attempt to work with other OS's--it just   takes over the entire system.  Since Ubuntu allows you the choice to dual-boot, the install becomes a little more complicated because there is partitioning involved and the need for a bootloader.

Just a thought, but in the next screen of the installer after you select partitions and mount points for root, swap and so on, are you checking the boxes to format the partitions you selected for root and swap?  It isn't clearly explained that you need to do this.

---

### Post by Netspeed on 2007-03-08
That's true about Windows taking over...just like AOL:( 

I don't think I did the formating after the partitioning. I'll give it a shot. Thanks!

---

### Post by gabng on 2007-03-08
I can confirm the problem of the live cd installer not recognizing selection of the root partition as well.  I ended up installing ubuntu using the alternate cd.

---

