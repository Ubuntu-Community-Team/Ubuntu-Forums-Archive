---
title: "could use some assistance on setting my hdd to dual boot 2 different linux OS"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by sinister_nation on 2010-09-09
I would like first to say, I switched to ubuntu from windows 7 about a week ago, and I don't regret it. there are things I do like to do and after doing some researching I'll be sticking with Ubuntu but I would like to have a second linux installation, and that would be Ubuntu Studio. Ubuntu Studio I would use for Multimedia purposes, like dvd editting, creating, import pictures from my camera and work with the pictures in ubuntu studio. and i might dabble around with audio.

while using Ubuntu for everything else. I do have a 1TB HDD in my computer (my ex-windows 7 HDD). I just need help with partitions I know i would need the following

/
/home
/swap

but I want to have these partitions also but be able to share between the 2 different OS's
/home/username/Videos
/home/username/Pictures
/home/username/Music
/home/username/Downloads

or should I just make a partition and call the partiton those particuliar storage and mount them in the OS's.

Then it comes to the grub. I know ubuntu uses grub2, so after I install the second linux OS would grub automatically configure it with the first linux or is this something that has to be done manually. If so then I need to know how to do that.

To do this would I need to download the alternate iso's, because I read that i would need at least 2 primary partitions. I know with the live cd's in the manual partition setup it only let you set 1 primary partition or I just re3ally haven't played around with it that much since last week.

Doing something like this isn't really for a newbie to linux, but I want to, because I don't have any desire to return back and use any microsoft OS's.

---

### Post by oldfred on 2010-09-10
I like to manually partition in advance so I know what is where. This requires a little planning in advance. And then you use manual install and choose which partition is / (root) and which is /home and what format each is. If /home exists you DO NOT format it. It finds an existing swap on its own.

I prefer data partitions. I started with a shared NTFS partition with windows which I still have but most of my data is now in a /data partition which has all my folders from /home. With all my data out of /home I now keep home as part of root as it is only about 1GB of hidden folders & files and easily to back up. I have about 6GB in root and create several root partitions for Ubuntu. I keep my old install, have my current and another for testing the beta. I have one or two unallocated 20-25GB partitions for additional roots incase I want to experiment and have created scripts to mount data and reinstall apps in each new system I install.

I used to mount my /shared into /home but with my /data partition I mount it in system and link each folder into /home so it looks like normal but all data is elsewhere.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I do this in my script
rm -rf Documents/
rm -rf Downloads/
etc
I then mount in fstab my /data  to mount points I create as /usr/local/fred/data and give it permissions and ownership to fred.

I used to do this.
#ln -s /usr/local/fred/data/Music
#ln -s /usr/local/fred/data/Documents

But running this from home creates links for every folder in /data
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

---

