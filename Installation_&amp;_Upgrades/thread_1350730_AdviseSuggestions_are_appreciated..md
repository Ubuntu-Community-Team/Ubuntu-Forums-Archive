---
title: "Advise/Suggestions are appreciated."
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Scholar-code on 2009-12-09
Fore mostly, My *nix experience.
I used Linux Red-Hat in the year 2005. But, I was just trying it out. And, I did not continue with it, because of some[May be stupid] issues. And, then I used Fedora 8 for couple of months may be for 8 months and even that on VMWare, and used Backtrack for misc stuffs.

So, I know the basics and I am little intermediate level of using Linux. And, now I am running, ubuntu 9.04 and little amazed and got very much interested with it. As I just installed it for trying it out and taught same kind of *nix distro and honestly admitting it, I really taught, that I am going loose the interest in this at very soon as the way I did with other distros, but, loosing interest is nothing, I got more and more interested in ubuntu. And, I did not even touch my windows partition from long time. Thanks to ubuntu for getting me away from painful windows restrictions and mercy-less ruling of Microsoft.

As, I said, I did installed it for giving it a try, I made a seperate partision of 15GB and installed ubuntu. And every thing on / (complete 15 GB) and yes, I did mounted the other partitions of my hard disk with fstab. But, I am little un-comfortable with the current setup of OS structure.

Now, Can any one suggest me a beautiful installation procedure keeping security in mind. [Yes, I did goggled, still I need few advices from the people who are very familiar with *nix world]

What exactly I mean is:


I have a 200GB of Hard disk, and I think of installing ubuntu in a more professional way. Which is going to be a very good experience and learning. So, I want to install it by making different partitions, like separate /boot, /, /tmp and /var/tmp etc. So, I am going to use 100GB for ubuntu. Rest of 100GB is already partitioned and I don't want to disturb the data over there. I can format this two separate partition, 80GB and 40GB into one 100GB partition and going to install ubuntu on it. How much space should I be providing for these separate /boot, /, /tmp etc partitions for avoiding any inconvenience in future. With upgrades/updates.

And also please provide me the appropriate tools/application for further learning. Like AppArmor, it was interesting read on the sticky, which is similar to SELinux. And, ufw/firestarter etc.


Suggestions are appreciated.

Thanks.

---

### Post by audiomick on 2009-12-09
Hallo,
For most people, the following is all you need.

/ about 10 - 15GB
Swap  a bit bigger than your RAM
/home  the rest of the available space

The / partition on my machine, with Ubuntu studio on it, updated 3 times, and everything installed that interest me, has about 6GB in it. I recently installed a standard Ubuntu for a friend. The / partition had about 2.7GB in it.

Swap needs to be as big as your RAM for the suspend and hibernate functions to work.

A seperate /home partition means you can simply remount it if you do a fresh install. This allows you to keep all your data and configurations.

---

