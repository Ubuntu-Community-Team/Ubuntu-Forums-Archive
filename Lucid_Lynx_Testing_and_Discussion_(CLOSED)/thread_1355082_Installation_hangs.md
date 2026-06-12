---
title: "Installation hangs"
date: 2009-12-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 3volution3 on 2009-12-14
When im trying to install Ubuntu 10.04 on my sony vaio at some part loading the installer (after few things written there) says something like "0% Detecting file system" and then screen goes black and then blinks all the text that was writen before and black again and then blinks, etc... never goes further. If i try a live session it doesnt load the live session either.
I have 1 partition with win7 and some free space.

What could be the problem of it?

---

### Post by 3volution3 on 2009-12-15
I used to use ubuntu on vmware and now i wanted to try on laptop but... im getting hopeless.

---

### Post by cubeist on 2009-12-15
> **3volution3 said:**
> When im trying to install Ubuntu 10.04 on my sony vaio at some part loading the installer (after few things written there) says something like "0% Detecting file system" and then screen goes black and then blinks all the text that was writen before and black again and then blinks, etc... never goes further. If i try a live session it doesnt load the live session either.
I have 1 partition with win7 and some free space.

What could be the problem of it?

This is alpha software.  This is to be expected.  Try a clean install with the alternate text based install.  Or stick to Karmic until your hardware is better supported.

---

### Post by jerrylamos on 2009-12-15
> **cubeist said:**
>  .... stick to Karmic until your hardware is better supported.

How does that get anything tested?  How do the developers find out about lucid problems if we all stick to karmic?

That said, I double boot karmic and lucid....lucid to see what's broken with this or that update, karmic (NOT UPDATED) when I want to get something done....

Jerry

---

### Post by cariboo on 2009-12-15
> **jerrylamos said:**
> How does that get anything tested?  How do the developers find out about lucid problems if we all stick to karmic?

That said, I double boot karmic and lucid....lucid to see what's broken with this or that update, karmic (NOT UPDATED) when I want to get something done....

Jerry

cubeist was looking at the op's join date and number of posts. He just joined the forums and only has 5 posts, that is an indication of a fairly new user. It is not recommended for them to start testing without more experience using Ubuntu.

---

### Post by 3volution3 on 2009-12-16
I use ubuntu to university to program C, java, etc but I also like to try out new systems and keep up with new technologies and development, that is why I am trying Lucid. Anyway I use Intel ICH8 system with a normal sata disk so I am not seeing how can I have compatibility issues. I can't try a clean install or not because it stops when trying to detect file system, the installer doesn't even load. Actually I was loading CD on boot with the intention of make a clean install in a new partition. Anyway I will try alternate install and if doesnt work I guess all I can do is install Karmic and upgrade to Lucyd (assuming that the Karmic will install in my system). I hope upgrade doesn't affect much the performance.

---

### Post by ranch hand on 2009-12-16
You should also keep trying the daily builds.  They may load for you.

---

### Post by VMC on 2009-12-16
> **3volution3 said:**
> When im trying to install Ubuntu 10.04 on my sony vaio at some part loading the installer (after few things written there) says something like "0% Detecting file system" and then screen goes black and then blinks all the text that was writen before and black again and then blinks, etc... never goes further. If i try a live session it doesnt load the live session either.
I have 1 partition with win7 and some free space.

What could be the problem of it?

How are you letting Ubiquity install;wipe the hard drive and install, auto partition the hard drive and then make space or manual?

I always do a Manual install. I have the partition already set up for use. You can do this several ways. The easiest is using gparted.

---

### Post by 3volution3 on 2009-12-17
Let's see if i make myself clear. What I've been trying to say is that Ubuntu CD doesn't load. I boot CD and choose to install and then appears for a while a symbol in the middle of screen while CD is loading, then appear cmd say 0% Detecting file system. I can't choose any partition because it never reaches that part and i can't use gparted because doesn't even load a live session. I'll try it tomorrow in weekend when i'm home and i'll see if other build or alternate or anything works.

---

### Post by cariboo on 2009-12-17
As a work around mount your hard drive to /mnt, and then start the installation process again. The partitioner should ask you if you want to unmount the drive. say yes, and your drive should be detected.

---

### Post by cubeist on 2009-12-18
Try the alternate CD (Text based installation) and do a clean install.  In my experience clean installs for alpha and beta versions cause the least amount of problems  The GUI install has been causing problems for many people.  Especially if you have Nvidia graphics.

---

### Post by 3volution3 on 2009-12-19
Alternate CD installed fine if i choose GRUB to install to MBR because if i choose to its own partition gives fatal error. After i the error i reinstall Ubuntu with GRUB to MBR i lose my windows 7 MBR permanently, no recovery possible so now i use GRUB, so far no problem because windows 7 appears in GRUB. Finally the time to turn on Ubuntu system, it hangs even before appear any screen. After that, i try recovery boot and it hangs. After a while appears a screen where i can do some crap or run Ubuntu in text mode... I guess i'll have a long time to wait until comes out a Lucid version working for me... I about to give up, format laptop and go back to vmware.

---

### Post by ranch hand on 2009-12-19
When you get to the "text crap" there is a menu (usually).  Select "dpkg fix broken packages" and hit enter and let it do its thing.

When it is done it will prompt you to hit enter which will return you to that menu.  Take the first choice "return to normal boot".  This will give you a CLI log in where you need to enter your user name and then your password.

You will then get a CLI prompt and type "startx".  If all is well you will be into your system in a normal manner.

If not do the same thing once a day and it will straighten out as dpkg updates your system.

If you get in and then can't the next day, go the same route but just hit the "return to normal boot" choice and see if that gets you in without the dpkg option.  If not you can start over and go that way.

I like to update through synaptic and apt rather than with Update Mangler on my "stable" OS'.  I would not use UM in testing.

If you are nervous use apt as it is pretty conservative in what it will update.  If you see something held back that you want to upgrade you can do that easily with synaptic.

Read the thread on UM and "partial upgrades" in the stickies of this forum.  You will find a lot of good ideas for different ways of upgrading in testing.

Expect breakage anyway.  Just try to keep it to a minimum.

Another important thing to do when you have problems is to remember to breath and think.  I have a temper and have trouble with that at times.

And most important, no matter what is going on, have FUN.

---

### Post by zika on 2009-12-20
> **ranch hand said:**
> When you get to the "text crap" there is a menu (usually).  Select "dpkg fix broken packages" and hit enter and let it do its thing.

When it is done it will prompt you to hit enter which will return you to that menu.  Take the first choice "return to normal boot".  This will give you a CLI log in where you need to enter your user name and then your password.

You will then get a CLI prompt and type "startx".  If all is well you will be into your system in a normal manner.

If not do the same thing once a day and it will straighten out as dpkg updates your system.

If you get in and then can't the next day, go the same route but just hit the "return to normal boot" choice and see if that gets you in without the dpkg option.  If not you can start over and go that way.

I like to update through synaptic and apt rather than with Update Mangler on my "stable" OS'.  I would not use UM in testing.

If you are nervous use apt as it is pretty conservative in what it will update.  If you see something held back that you want to upgrade you can do that easily with synaptic.

Read the thread on UM and "partial upgrades" in the stickies of this forum.  You will find a lot of good ideas for different ways of upgrading in testing.

Expect breakage anyway.  Just try to keep it to a minimum.

**Another important thing to do when you have problems is to remember to breath and think.  I have a temper and have trouble with that at times.**

And most important, no matter what is going on, have FUN.Boy, once I've learned myself just to take this into equation, it made testing more easier and less life threatening ... I can only say that I'm now seriously considering that action, not that I'm able to resort to that, every time a problem threatens to pierce its ugly head ...

---

### Post by VMC on 2009-12-20
> **ranch hand said:**
> When you get to the "text crap" there is a menu (usually).  Select "dpkg fix broken packages" and hit enter and let it do its thing.

...

Expect breakage anyway.  Just try to keep it to a minimum.

Another important thing to do when you have problems is to remember to breath and think.  I have a temper and have trouble with that at times.

And most important, no matter what is going on, have FUN.
I take the conservative approach and haven't had any problems for the last two testing cycles;9.10, 10.04.

I use: sudo "aptitude update && sudo aptitude safe-upgrade", and I rarely have any issues.

 When I run across items that are held back, I leave them alone. Eventually, they get updated.

---

### Post by 3volution3 on 2009-12-29
Updates not working so I will just format my laptop and use Ubuntu in vmware again to get Ubuntu disk space back and have the back the win7 boot loader that is faster than grub to start up :)

---

