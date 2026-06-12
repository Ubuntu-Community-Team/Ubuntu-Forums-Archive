---
title: "issue in instalation"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by aragorn the strider on 2011-04-30
[B]hi friends,
 Am new to ubuntu,once i tried suse.Yesterday I installed ubuntu ,but I was facing some problems.
In detail...

I have 500 gb HDD already using windows ,the problem is I created 120 GB ext 2 partition ,so how much memory should i issue to each file i.e / ./home./vsr, /home etc..After a long fight I installed ubuntu but when I tried to play some MP3 its showing error.


Please help me out.[/B]

---

### Post by aragorn the strider on 2011-04-30
atleast give a link for starters installation guide,so it will be helpful to me..
Thank you

---

### Post by manzdagratiano on 2011-04-30
Your stating "its showing error" is not really helpful to debug your problem. And you have multiple issues in a single post.

That being said, take a look at the following page:

[https://wiki.archlinux.org/index.php/Beginners%27_Guide#Partition_Scheme](https://wiki.archlinux.org/index.php/Beginners%27_Guide#Partition_Scheme)

which will help you understand details about the partitioning scheme. I personally use the following:

/boot - 128 MB partition
/       -  30 GB partition
rest of the drive - a third partition for the rest of my data

It is not really a good idea, at least in my opinion, to install /usr, /var etc on their own partition, since they might get filled up and you may run out of space, or you might end up wasting extra space for no reason. People have their own preferences though.

Regarding your mp3 issue, I am guessing that since you have a new install, you need to have the gstreamer plugins from the 'bad' and 'ugly' families installed. You may do that from the software center - search for gstreamer and install the gstreamer0.10-plugins-bad-universe, gstreamer0.10-plugins-bad-multiverse (and the same for ugly) packages, and also install ffmpeg. This should get you going with your mp3's. Since mp3 is a proprietary format, its support is not enabled by default.

---

### Post by aragorn the strider on 2011-04-30
thank you very much mate.

---

