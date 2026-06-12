---
title: "200Mhz... can it be done?"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by deamon on 2005-07-16
I've just got an old RM box, 200Mhz, 2GB HDD, I think it only has 32MB RAM SD. Do you guys recon I could get Ubuntu to run on it? Or do you know of any other linux distibution that can be run on such an old system?


Thanks!

---

### Post by dave9191 on 2005-07-16
Do you want to run a linux distro on that as a desktop machine or some kind of server ? 

Linux will run on that, but you might have poor performace when it comes to gnome or kde and you might have to resort to a simpler window manager like fluxbox. 

Dave

---

### Post by bored2k on 2005-07-16
[QUOTE=deamon]I've just got an old RM box, 200Mhz, 2GB HDD, I think it only has 32MB RAM SD. Do you guys recon I could get Ubuntu to run on it? Or do you know of any other linux distibution that can be run on such an old system?


Thanks![/QUOTE]
 BEAtrix Linux or DSL

---

### Post by WildTangent on 2005-07-17
the only way Ubuntu will work on that is with a server install, trust me, ive tried, and (obviously) failed

-Wild

---

### Post by damonw5 on 2005-07-17
[QUOTE=WildTangent]the only way Ubuntu will work on that is with a server install, trust me, ive tried, and (obviously) failed

-Wild[/QUOTE]
 I'd try a minimal distro like D(arn) Small Linux on it.

However, if you could get another 32mb of RAM off of ebay or something, it would make a world of difference!

---

### Post by deamon on 2005-07-17
[QUOTE=damonw5]I'd try a minimal distro like D(arn) Small Linux on it.

However, if you could get another 32mb of RAM off of ebay or something, it would make a world of difference![/QUOTE]

First of all, thank you all for your replies!!

I have another machine up at uni -  an old AMD box with two 32MB SD modules I could canabalise out of it. I have two free slots in the 200Hz box so they should fit nice. 

While I've been installing I've been getting this error;

Install starts no problem, I get to the point where it says "retreiving nic-firmware -2.6.10-5-386-A" and the computer gets stuck in a constant loop between retrieving and unpacking this nic-frameware at 1%. Is this to do with the low memory? I've installed Ubuntu no problems on an XP box, this (new) old one tho was currently running windows 98, but I believe the machine is an origianal "windows box" 'tm' for the origianal distribution of win 95.  ](*,) a

---

### Post by broschb on 2005-07-17
I would try vector linux, i've tried DSL linux and prefer vector linux more.  I have it running on an old 233mhz laptop with 32 MB ram.

---

### Post by mingus on 2005-07-18
I have a Ubuntu Pentium 133Mhz box that I primarily use to test installations.

The 32MB is cutting it razor thin, and on some boxes, is not enough to even install.  I was able to install by pre-partitioning the disk and creating a swap.  And of course, 32MB is not sufficient for gnome or kde, nor probably even xfce.  But windowmaker or fluxbox might work.  (I added RAM to this box for this reason.)

Your other consideration is the 2GB hdd.  You will really have to trim down what you install.

Vector is a good alternative, as was suggested.  It's based on slackware, does have a sort-of configurator, comes with the lightware window managers.  With old hardware, don't be surprised that you may have to fiddle quite a bit with X.

---

### Post by deamon on 2005-07-19
Thank you all for your great help! Yea the 32 SD RAM is pushing it LOL. But it was free so I can't complain! I've got DSL working fine on it now, just trying to get the gcc to work on it... i see the sudo awt-get update doesn't work on DSL straight away, may have to do a bit of fiddling.  :grin: 



D

---

### Post by deamon on 2005-07-19
P.S. 

The feature on DSL where you can boot any machine into it with the CD ROM without tutching the HDD is cool as [IMG]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/IMG]

---

### Post by az on 2005-07-19
There is the ubuntu-lite project which aims to give you something for a machine such as your's.  It is aimed for 200Mhz CPU with 64 megs of ram, though.

For now, you can either use a shipit CD or a carefully burned downloaded cd, since older cdroms sometimes have trouble with the 2.6 kernel on the installer.  The cd has to be perfect.

Also, use a server installation, or use the 
linux archive-copier/copy=false 
option or you will run out of hard drive space with a 2 gi hard drive (you will lose some of that to a swap space and filesystem data, so you do not even have 1.8 gigs....)

---

