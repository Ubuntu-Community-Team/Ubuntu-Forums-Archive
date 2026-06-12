---
title: "Best Ubuntu options for my needs?"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by jefferson411 on 2010-11-01
Hello all,
I am a new user to Ubuntu, I have really enoyed my experience using it so far but my main purpose for using it has been school work. I recently converted an old desktop to run Ubuntu, but due to the need to often be on the move I would like to pull my laptop out and program between classes or whenever I am unable to get to my desktop or the school lab. However, I do not necessarily forever want this laptop to have several gigs dedicated to Ubuntu. So my question is, is there a way to partition about 10-15 gigs for Ubuntu and dual boot for now, then return the partition to Windows 7 sometime in the future?
 
I have been booting from CD into Ubuntu 8.04 but frequently when I attempt to do this I am met with an error message, so I would like to have a reliable way to boot into Ubuntu. This method has been frustrating anyways because I always have to reinstall gnu compilers and re-add files either from a flash drive or downloading them. I thought about running as a virtual system within Windows 7 but I suppose I would have the same issues, is there a way to make no changes to my laptop but still have an Ubuntu image with all the changes I made last time I used Ubuntu? I read something on wikipedia about virtual burning, I didn't know if thats what I wanted.
 
tl;dr I need to have a continually changing version of Ubuntu that I can either run or boot to but am wondering if I can avoid partitioning my laptop or if I can return the partition to Windows 7 when I am no longer in dire need of Ubuntu on the go. 
 
Thanks for any help, I know its a lot to ask on my first post but I plan on contributing as much as I can as I learn more about how Ubuntu works.

---

### Post by Megaptera on 2010-11-01
10-15gb would be sufficient, you can create free space using GParted from live CD then install Ubuntu to that.
When it comes to removing Ubuntu, guide here:
[http://ubuntuforums.org/showthread.php?t=272313](http://ubuntuforums.org/showthread.php?t=272313)

Hope this helps?

---

### Post by jefferson411 on 2010-11-01
Thank you, that post was exactly what I was looking for. I think I'm going to go on and go through the process of setting up dual boot seeing as I have been trying to work on my compiler project for the last hour and have not been able to boot into Ubuntu from  a disc on my Vaio the entire time. Thanks for the help!

---

### Post by Megaptera on 2010-11-01
You're welcome!!

---

### Post by jefferson411 on 2010-11-02
I return with more questions, I figured I will keep going here rather than litter with a new post:

I am using this guide [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) for my attempt to install ubuntu side by side with Windows 7, and used the linked How To Geek article about Windows shrink volume problem, but I have questions before I muck anything up: if g-parted is going to partition my hard drive why am I shrinking the volume first? And also, after trying the suggested fixes windows will still only let me shrink the volume by 2 gigs, despite having 33 gigs free. The defraggers all show my MFT at the end of my free space so I assume it is 2 gigs away from the end of the volume. How can I move the MFT or is it even necessary to shrink the volume before I partition? I lost my Windows 7 disc so a fresh install of both OS'es is not possible.

---

### Post by Megaptera on 2010-11-02
Before you go any further, have you backed up to external media all your docs, vids, photos etc etc - just in case??

Could you post a screenshot from Gparted using live CD (try Ubuntu not install Ubuntu!!) showing the current setup and how the space is used? If there's only 2gb free that's not enough for Ubuntu

---

### Post by jefferson411 on 2010-11-03
[http://imgur.com/2DpCF.png](http://imgur.com/2DpCF.png)

That shows my free space and recovery partition. I know parted will let probably let me make a 15 gig partition, but what threw me off was the tutorial telling me to shrink the partition first, I don't see the point if I'm just going to chop of 15 gigs.

Yes I have backed up my drive using DriveImage XML.

---

### Post by Megaptera on 2010-11-03
Thanks.
I'd let GParted do it as Vista didn't want to. As you say, there's plenty of spare space there.

---

