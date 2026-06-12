---
title: "LXDE on Samsung Galaxy S"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by rvndmnmt on 2012-09-14
I'm getting ready to drop this phone off of my plan.  It's been a steady companion over the past 3 years.  Even got this thing running on Jellybean right now.  The problem is that I can't afford a $220 a month phone bill for three lines when I only need two at the moment.  And the old girl is still my main workhorse even over my Galaxy S2.  So I plan on keeping this thing.  Besides, have to get some use out of the 2300Mah battery I bought for it.  That being said, I bought this thing because I like physical keyboards and the keyboard in question is actually big enough to use.  

So this is hypothetical.  More like a brain storming exercise.  I had Linux running on my PS3, why not a mobile device?  I want an actual install, none of this VNC crap.  The system is not strong enough.  For actual specs were talking about this:

CPU: 1 Ghz Snapdragon processor
RAM: 512Mb
Internal memory: 1 Gig
External memory: 16 Gig

Asides from the 5 Megapixel rear camera and 3 Megapixel front camera, GPS, and integrated WI-FI.  We are talking about a high end Pentium 2/low end Pentium 3 system from about the 98-99 era.  Compared to today's computers.....not so great.  But for a hand held device......still not so great.  But adequate enough.  The keyboard and touch screen should provide the necessary inputs I need for basic operation

Given these stats I just don't think the latest edition of Ubuntu would run very good though the Unity desktop even though it would be better suited for the task.  Given my past experience with compiling an ESUS eee 2gsurf under similar circumstances I decided to go with LXDE even though XFCE would probably be the better option.  Problem is I don't like XFCE.

My 2g surf project was an effort to turn a cheap piece of plastic into a device we could use to diagnose some of the older elevators we work on.  The power was similar, 800mHz vs 1 ghz.  The RAM situation the same at 512Mb.  The memory situation is very similar as well.  The eeepc had 2 gig of internal memory, the Galaxy 1 gig.  So, in a way, this isn't my first rodeo.  What is different is the ARM architecture vs the X86.

I've still got all my notes for the eeepc project.  I already know that I am going to have to get "creative" with my partitioning.  Swap is going to the internal chip due to the internal chips durability, that's going to take half of it.  I figure I should have enough room for one of the more used partitions, maybe two.  That should extend the life of the SDMicro card greatly.  The eeepc is still running on the SD card I installed on it is still going a couple years later.  But this is not something used daily.  So I figure that I should get about 6-8months of use out of the card before it wears out.  Maybe up to 12.  So backups are a must.  There wasn't much room on the eeepc so I had to keep up on housekeeping.  I imagine it's going to be the same here.

So, it comes down to the architecture.  Android runs on the Linux kernel the same as Ubuntu.  Thing about it is that I have no idea as to the internals of Android.  I figure I might be able to chuck LXDE desktop in place of Android.  But this isn't the eeepc.  I installed the basic Ubuntu kernel on the eeepc and then built up.  This is something I am probably going to have to build in an SDK then use Clockwork Mod or some other comparable recovery app to install.  Near as I can tell Ubuntu just doesn't support my device for ARM so I am probably going to have to use the latest stable kernel for Android and build on that. But then there are the libraries for the individual programs I plan on using.  Whenever I build a system I tend to go with, what I have found through personal use, what works.  So the desktop may be LXDE but I am going to have libraries from Gnome and KDE installed to support the additional programs I have installed on it.  

So, am I on the right path?

---

