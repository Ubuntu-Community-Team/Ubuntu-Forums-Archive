---
title: "no luck creating good install CD"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by piperguy on 2010-10-15
I have a couple of older Dell systems that I want to install Ubuntu 10.10 with.

But when I insert the CD that I burnt and then reboot, the Ubuntu installation either crashes or just does not install properly and the machine just hangs. I've used both: a CD-RW and a CD-R and they both don't work.

As a test I re-installed Windows XP from an installation CD on one of the machines without any problem. I also found a complete Centos installation on CD that I had kicking around and I was able to install it on the other machine, again with no problems. 

Yes I burnt the CD at the slowest possible speed. What else could be wrong?

thanx
/carl h.

---

### Post by Skaperen on 2010-10-15
Other possible problems:

1.  The download you are burning from is bad.

2.  Something about that machine is not quite right, such as RAM or hard drive.

Can these two machines run applications OK when using the trial/live selection of Ubuntu booting from those disks?  If so, try the install application icon on the trial/live desktop and see if that has any better luck.

---

### Post by dhavalbbhatt on 2010-10-15
> **piperguy said:**
> I have a couple of older Dell systems that I want to install Ubuntu 10.10 with.

But when I insert the CD that I burnt and then reboot, the Ubuntu installation either crashes or just does not install properly and the machine just hangs. I've used both: a CD-RW and a CD-R and they both don't work.

As a test I re-installed Windows XP from an installation CD on one of the machines without any problem. I also found a complete Centos installation on CD that I had kicking around and I was able to install it on the other machine, again with no problems. 

Yes I burnt the CD at the slowest possible speed. What else could be wrong?

thanx
/carl h.

Hi Carl,
Welcome to the club. I have been having the same issues - I have wasted about 7 CDs on just trying to create a good 10.10 64bit installation CD and none of them have worked. 

What I am trying right now is burning the DVD version of 10.10 and seeing if that will help or not. If it does, I will come back and update this post.

As an alternative, what you can also do is, try out Kubuntu - maybe that will work. If not that, then you might be able to try one of the variants and see if that works. 

If you do have a USB drive, then also try to install it using the USB drive.

Last, but not the least, try installing 10.04 and then do an upgrade to see if that works.

I feel your pain though. 

Have fun,
Dhaval

---

### Post by 1Dagars1 on 2010-10-15
One thing i tried that worked for me was to download and burn (at the slowest speed) the .iso from within Ubuntu 10.04. I burned multiple cds from within windows that did not work but the first try from 10.04 worked for me no problem.

---

### Post by piperguy on 2010-10-16
All good advice which I'll try. The machine was my daughters and worked fine with Windows, so there isn't a hardware issue.

One thing that has changed since my last post. After my 'n'th time trying to install on my Dell GX150, it seemed to install as I was prompted with questions that I hadn't been prompted with before. It went all the way with the installation and after I rebooted it prompted me to login. After logging in it started providing a desktop, but then it froze. 

I rebooted and logged in in 'safe mode' and presto, I got a desktop without freezing.  In fact I'm updating this thread now from within it. Seems to be working time.

1. Any ideas why non-safe mode won't work?

2. What can't I do in safe mode?

3. Is there a way to force a network re-install of 10.10 from 10.10 ?

(I love Ubuntu, but what a struggle to install!)

thanx
/carl h.

---

### Post by piperguy on 2010-10-22
Hmmm...no responses. 
 
I tried burning 10.04 from Ubuntu instead of Windows and did an install, after which I upgraded to 10.10. Still the same; can't get a desktop unless I'm in safe mode.
 
I'm going to post to the mailing list.
 
/carl

---

### Post by confused57 on 2010-10-22
It's probably a problem Ubuntu has with your video card, here's some suggestions from oldfred that might help:
[http://ubuntuforums.org/showpost.php?p=9586925&postcount=7](http://ubuntuforums.org/showpost.php?p=9586925&postcount=7)

---

### Post by efflandt on 2010-10-22
Two possible issues that can crop up on older computers with Ubuntu 10.04 or 10.10.

1. The default for 10.04 or newer ATI or nVidia default drivers is kernel mode setting (KMS) video drivers instead of previous user space modules.  Some older video does not like KMS.  You can get around that using **nomodeset** kernel boot parameter.  [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

2. Default partitioning for 10.04 or newer is on MB boundaries instead of cylinder boundaries.  But if that is an issue, you probably would end up in grub rescue instead of even getting to the grub menu.  If you need to work around that you might need to use **partman/alignment=cylinder** and/or if you use gparted to create or remove/recreate your partitions, you may need to check the box in that to align to cylinder boundaries.  [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems)

---

