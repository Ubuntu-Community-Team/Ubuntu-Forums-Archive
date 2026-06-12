---
title: "Even the experienced struggle! Cloning previous Ubuntu Installs?"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by It_Was_Luck on 2008-11-25
Well personally I'd consider myself pretty good with Ubuntu. I got my first box up and running around last year and actually wrote a full tutorial on how to skin your Ubuntu machine to look like a Mac... and thats where I come in need.

See this is what my set-up was:
80GB Harddrive
-70GB Windows XP Partition
-8GB Ubuntu Partition
   -2GB Swap Partition

So I went out and bought a new 80GB drive and really really wanted the EXACT SAME Ubuntu system on my new hard drive, so I considered cloning programs but none of them would help me to take the EXACT install I have on that 8GB and put it in the 76GB of space I'm providing. I say this because I had used Ubuntu so long, my desktop and settings and everything had been so precisely tweaked that I just couldn't take another stab at it.

If you know how to do this I'd love your help.

Cheers.

---

### Post by VastOne on 2008-11-26
1: If you do not have a /home partition, create one using this method

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

2: Get and use remastersys to make a Live CD and use it to install on the new drive.  Make sure to partition everything the way you want it and make sure you use the manual install selecting a / partition, a swap partition and your new /home partition.  Make sure you format the / and the swap BUT NOT THE /HOME PARTITION.

I just went through all of this and am now very happy with the results.

search VastOne and you will see some of my trials, and contact me if you need any more input..

Good Luck

Vastone



> **It_Was_Luck said:**
> Well personally I'd consider myself pretty good with Ubuntu. I got my first box up and running around last year and actually wrote a full tutorial on how to skin your Ubuntu machine to look like a Mac... and thats where I come in need.

See this is what my set-up was:
80GB Harddrive
-70GB Windows XP Partition
-8GB Ubuntu Partition
   -2GB Swap Partition

So I went out and bought a new 80GB drive and really really wanted the EXACT SAME Ubuntu system on my new hard drive, so I considered cloning programs but none of them would help me to take the EXACT install I have on that 8GB and put it in the 76GB of space I'm providing. I say this because I had used Ubuntu so long, my desktop and settings and everything had been so precisely tweaked that I just couldn't take another stab at it.

If you know how to do this I'd love your help.

Cheers.

---

### Post by It_Was_Luck on 2008-11-26
Thank you for your help but let me ask a little before I go ahead and execute.

I was told awhile ago a /home partition is nice, but not necessary so I've never looked that direction, but I always thought if I was going to make one, I'd be able to just create it in the partition manager during install.

Now if I'm following you correctly... you want me to take my CURRENT Ubuntu install (which I want to copy) and make a /home partition using your method.  Then this program, remastersys, can copy my CURRENT Ubuntu install, and when I pop it in my computer with the news 80GB hard drive, it'll allow me to install the EXACT same set-up of Linux I had on my old drive?

Thanks for the help.

Edit: Regarding the home folder... see, I really don't have many files I really need on my other system. I basically want everything the same, but if I'm missing some files, its okay, I'll just move the important ones to a flash drive and back over in my new install... with this eliminate my need for a /home partition?

---

### Post by VastOne on 2008-11-26
I was in the same position you are in, really liking my tweaks to my current system, which is what led me down this path.

Regarding the /home partition, if you ever want to run a new install versus an upgrade of Ubuntu in the future, or test any other flavor of a Distro, that in itself is enough to have the /home partition as your current settings will not be affected and you can carry (share /Home) the settings to the new install or test any new Release Candidates or Beta's in the future.

I set about all of this to "see" if a new install of Ubuntu 8.10 was any better than my upgrade of 8.04 to 8.10.  

I first went with just an install of 8.10 on a new drive using a new / (file system 100 gig) a new swap and using my already created /home in the new install.  I was very unhappy that none of my applications and tweaks (other than visual like fonts and backgrounds) came over in the new install.

I had already used remastersys in the past (8.04) to carry with me on Windows repair jobs I do that will not boot, so I was familiar with it.

I setup a new LiveCD/remastersys of my current (much loved) install of 8.10 and used it as my install cd and used the same settings (/ 100gig, new swap, same /home partition (no format)) and when I booted to the new drive (SATA2), everything I had on the SATA1 install was there and perfectly preserved, thus creating the ultimate Disaster recovery disk.

In response to your saying your are not concerned with what is in /home and that you could just copy it, all your tweaks and settings that got you your current setup, is held in your home and file system.

Having /home on its own partition preserves your personalized changes, using remasatersys moves over your file system in the new install.

One other note, this method also preserves all security settings and rights to your files and access points, which did not happen on the outright install I did of 8.10 on SATA2

Long winded I know, I apologize....

> **It_Was_Luck said:**
> Thank you for your help but let me ask a little before I go ahead and execute.

I was told awhile ago a /home partition is nice, but not necessary so I've never looked that direction, but I always thought if I was going to make one, I'd be able to just create it in the partition manager during install.

Now if I'm following you correctly... you want me to take my CURRENT Ubuntu install (which I want to copy) and make a /home partition using your method.  Then this program, remastersys, can copy my CURRENT Ubuntu install, and when I pop it in my computer with the news 80GB hard drive, it'll allow me to install the EXACT same set-up of Linux I had on my old drive?

Thanks for the help.

Edit: Regarding the home folder... see, I really don't have many files I really need on my other system. I basically want everything the same, but if I'm missing some files, its okay, I'll just move the important ones to a flash drive and back over in my new install... with this eliminate my need for a /home partition?

---

### Post by It_Was_Luck on 2008-11-26
Okay I just run remastersys on my current Ubuntu box and it finished but it came out kinda odd... there was a folder with a bunch of different files, which I assumed were all compressed into the final .ISO, well when I clicked on the .ISO of my system, it was only 22MB, and I'm reluctant to burn 22MB over to a LiveCD just for it to not work. Maybe you can put me down the right path again...

When I started up remastersys, I selected the first option "Back-up complete system including user data."

So when it was done I went in and this is what it looks like:
+remastersys
 -dummysys
 -ISOTMP
 -custombackup.ISO
 -custombackup.ISO.MD5
 -remastersys.log

But the .ISO is only 22MB, the dummysys folder is 296MB and the ISOTMP folder is a full 2.2GB... so how do I make a LiveCD out of that??

---

### Post by VastOne on 2008-11-27
You need to select the second option DIST Make a Distributable copy to share...

But first select the clean option to remove temporary files and then do the Dist option

That is the one that makes the LiveCD

Good luck...

VastOne

> **It_Was_Luck said:**
> Okay I just run remastersys on my current Ubuntu box and it finished but it came out kinda odd... there was a folder with a bunch of different files, which I assumed were all compressed into the final .ISO, well when I clicked on the .ISO of my system, it was only 22MB, and I'm reluctant to burn 22MB over to a LiveCD just for it to not work. Maybe you can put me down the right path again...

When I started up remastersys, I selected the first option "Back-up complete system including user data."

So when it was done I went in and this is what it looks like:
+remastersys
 -dummysys
 -ISOTMP
 -custombackup.ISO
 -custombackup.ISO.MD5
 -remastersys.log

But the .ISO is only 22MB, the dummysys folder is 296MB and the ISOTMP folder is a full 2.2GB... so how do I make a LiveCD out of that??

---

