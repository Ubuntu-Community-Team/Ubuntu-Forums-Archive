---
title: "Which version??  10.04LTS or 10.10?  upgrading from 9.04"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by dBuster on 2010-12-31
Okay, I have a NAS drive on its way and once it is here and installed I am going to do my backups.  I am also planning on creating a new partition for my /home and will migrate to that home partition.

My question, with the two versions mentioned, which will provide the easiest transition/install?

I am asking as I had a terrible time with this laptop getting a version to install on when I got it and ended up starting with 9.04 alpha which installed at that time.  Between getting the wifi up and working and then the nvidia and so forth I want to be able to upgrade, doing a clean install of course, without being down for a terribly long time, ie, wanting it to work after install, everything, including the wifi.  This is a compaq cq60-215dx which is a great laptop, just was a bear to initially get Ubuntu up and running well.

Any insight would be greatly appreciated!!!

Also, I want to have effortless use of the NAS also when upgraded...

---

### Post by SnickerSnack on 2010-12-31
You can't upgrade directly from 9.04 to 10.04.  You'd have to go 9.04 -> 9.10 -> 10.04, and then to 10.10 if you want.

With a clean install, I don't see any reason to go with 10.04 over 10.10.  Maybe I've misunderstood your question.

---

### Post by dBuster on 2011-01-01
> **SnickerSnack said:**
> You can't upgrade directly from 9.04 to 10.04.  You'd have to go 9.04 -> 9.10 -> 10.04, and then to 10.10 if you want.

With a clean install, I don't see any reason to go with 10.04 over 10.10.  Maybe I've misunderstood your question.

Yes you have misunderstood...

I am not upgrading as in one would think.  I am meaning upgrading with a clean install.

So with that cleared up, are they any benefits of 10.10 over 10.04??  Other than the LTS??  

9.04 is the first release I am running dating back to 6.04 that is not a LTS release and I am just looking to find out which of the two is better and why?  Hardware support being key with my nVidia graphics and atheros wifi need to work, preferably without my having to re-install/compile, after each kernel update as I had to with 9.04...

---

### Post by lithopsian on 2011-01-01
10.10 is the newest Ubuntu.  LTS just means it is the Long Term Support release.  You can get an LTS 10.04 if you want, but obviously that is six months out of date!

10.10 you may see referred to as Maverick, and 10.04 was Lucid.  Either is fine, but obviously 10.10 has a slightly newer kernel and so support for slightly newer drivers and applications.  Maverick also, by default, comes with a different looking desktop but there is nothing to stop you changing this.  With a fresh install I can't see any reason not to use the latest stable release,  If there is something horrible with support for your hardware (nVidia or Intel graphics drivers comes to mind!) then you can easily enough go to 10.04.

---

### Post by mörgæs on 2011-01-01
There is only a minor difference between 10.04 and 10.10. I would give both a thorough test in a live environment and pick the one who works best on your particular hardware, plain and simple.

---

### Post by dBuster on 2011-01-01
> **mörgæs said:**
> There is only a minor difference between 10.04 and 10.10. I would give both a thorough test in a live environment and pick the one who works best on your particular hardware, plain and simple.

Thank you for a reply, I have given both a try in a live environment.  Both function well.  I sort of like the 10.10 way of starting up and getting wifi running before anything else.  Thought that was pretty sharp.  Seeing things come alive before the desktop appeared.  But other than that, both versions did have no problems with my atheros wifi card, both need me to install the latest nVidia, which I figured I would have to.

I think though for the ease of updates, I am not one that has to get the latest release as soon as it is released, that is almost foolish.  But I do like the ability to easily update if I wanted to and if I skip one or two releases, at least with the LTS  I can go from one LTS to another without having any problems.  Skipping essentially those in between!

> **lithopsian said:**
> 10.10 is the newest Ubuntu.  LTS just means it is the Long Term Support release.  You can get an LTS 10.04 if you want, but obviously that is six months out of date!

10.10 you may see referred to as Maverick, and 10.04 was Lucid.  Either is fine, but obviously 10.10 has a slightly newer kernel and so support for slightly newer drivers and applications.  Maverick also, by default, comes with a different looking desktop but there is nothing to stop you changing this.  With a fresh install I can't see any reason not to use the latest stable release,  If there is something horrible with support for your hardware (nVidia or Intel graphics drivers comes to mind!) then you can easily enough go to 10.04.

hmm and before those there was???

6.06 LTS - Dapper Drake
6.10  - Edgy Eft
7.04  - Feisty Fawn
7.10  - Gutsy Gibbon
8.04 LTS - Hardy Heron
8.10  - Intrepid Ibex
9.04  - Jaunty Jackalope
9.10  - Karmic Koala

and after that the next flavor is...
11.04  - Natty Narwhal

With LTS you can go from one LTS release to another without needing to step through each release in between which is a major plus for someone who does not need to get the latest as it releases.  If it isn't broken, DON'T break it.  Having been using Ubuntu for oh lets see 4 years now... hmm very familiar with the naming...

---

### Post by perspectoff on 2011-01-01
I have found nothing in Maverick (10.10) that makes me want to update from Lucid (10.04). YMMV.

---

### Post by mörgæs on 2011-01-01
A small correction: 6.04 was delayed and ended being released as 6.06.

---

### Post by dBuster on 2011-01-02
> **mörgæs said:**
> A small correction: 6.04 was delayed and ended being released as 6.06.

Thank you for the correction.  I did not start using it until July of 06 so I just took it that it was an 04....  Any how...


> **perspectoff said:**
> I have found nothing in Maverick (10.10) that makes me want to update from Lucid (10.04). YMMV.

Thank you for the honest input.  I believe I am going to go the route of 10.04.1 for my install.  I appreciate another view.  Heck the way I am planning on doing it, if I have too many issues with 10.04 it would be a piece of cake to start over...

---

### Post by dBuster on 2011-01-02
Okay here is a good question...

Does Ubuntu have a means to make an image of a hard drive?  Meaning if I boot from a cd into live mode, can I create an image of my existing hard drive?

Before I go and do anything I am going to get my NAS setup and working and then back up my home and then I will partition my drive making the windows partition smaller as I simply do not use it, but keep it for when tax time comes since tax software doesn't run well in Linux, create a new partition for my home and then move my home over.  Once it has been tested and no issues I will then go ahead with a clean install keeping my home partition untouched.

So with all that on the table to do, I would like to have an image of what I have now just in case, you know murphys law, and then I can restore and try all over again.

---

### Post by mörgæs on 2011-01-02
Maybe Clonezilla will do the trick.

[www.clonezilla.org](www.clonezilla.org)

---

### Post by dBuster on 2011-01-02
> **mörgæs said:**
> Maybe Clonezilla will do the trick.

[www.clonezilla.org](www.clonezilla.org)

Sounds like a good choice.  Downloading now.

---------------------------------------------------------

Next question...  I have successfully reduced the size of my windows partition.  Now I have an unallocated space on my drive, however, if you look at the screen capture, it is before my Ubuntu partition. 

[IMG]http://ubuntuforums.org/picture.php?albumid=1154&pictureid=7298[/IMG]

Can I partition it as a primary and not ruin my boot to Ubuntu?  I am trying to do what I can prior to getting that NAS drive...

Or what is recommended for me?  Bear in mind that new partition is going to be used as my home partition.

---

### Post by mörgæs on 2011-01-03
Sorry, I don't know of that, but there should be plenty of guides (and threads) on Gparted available.

---

