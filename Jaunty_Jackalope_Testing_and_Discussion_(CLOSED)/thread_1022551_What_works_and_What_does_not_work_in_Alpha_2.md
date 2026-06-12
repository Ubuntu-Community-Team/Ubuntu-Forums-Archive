---
title: "What works and What does not work in Alpha 2"
date: 2008-12-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by obsrv on 2008-12-26
I wrote a small review of my first impressions on Jaunty Jackalope. Frist what I want to say, that wallpapers are awesome. I'm lovin them, no need of custom wallapers :) other thing is nice in wubi disk partitioning is great looking, sooooo groooooovy :) and theme DarkRoom is excelent :) just it cannot mount NTFS partitions outofthebox, but I have a workaround for it. And internet does not work (one ISP, I have two). Now I forced to use my servers Internet Resources, but it is OK for now, till full release. Strange because /etc/resolve.conf is empty after connectin cable from my first internet provider, and it is normally writen nameservers in resolve.conf when I connect the second one cable (ISP for Server "PIRATE"). Now the third this, Synaptic quick search (filter) is soooo awesome :) Cheers, what is your opinion about Alpha2 and please comment my problems, maybe together we will find solution :)

---

### Post by jerrylamos on 2008-12-27
Install manual partition doesn't work, for example, for the last week and a half of daily builds.  manual partition edit partition use as hangs ubiquity see launchpad bug 310982.  

I got this jaunty running by installing intrepid (trudge) and doing an upgrade (trudge).  I'd much rather test daily builds by rsync which just downloads the changes in the .iso then write a USB flash drive to "try" an install in a test partition.

Jerry

---

### Post by ShirishAg75 on 2008-12-27
Not able to see [lpbug]310982[/lpbug] . It says forbidden . It says 

**Not allowed here**

               Sorry, you don't have permission to access this page.   
        You are logged in as (with my username)

---

### Post by exploder on 2008-12-27
I checked out alpha 2 a couple of days ago. The release looks pretty decent so far. I hope the quality of the release stays on the current path! I noticed that the notifications feature is a work in progress but I like the idea and I think that the finished work will make things nicer for people that are new to Ubuntu.

I just want the Developer's to take their time and concentrate on bugs and regressions. So far things are looking up!

---

### Post by obsrv on 2008-12-27
Can't find release schedule for Jaunty, when there will be Alpha 3? Sorry that I can't find thins info by my self :)

---

### Post by luca_linux on 2008-12-27
> **obsrv said:**
> Can't find release schedule for Jaunty, when there will be Alpha 3? Sorry that I can't find thins info by my self :)
[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

---

### Post by obsrv on 2008-12-27
> **luca_linux said:**
> [https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

Thank you, I don't know how I didn't managed to find it :lolflag:

---

### Post by luca_linux on 2008-12-27
> **obsrv said:**
> Thank you, I don't know how I didn't managed to find it :lolflag:
No problem. ;)

---

### Post by Gina on 2008-12-27
Just tried Alpha 2 Desktop install on my laptop - no joy.  Problem at partitioning - setting root partition dialog - the dropdown boxes don't work.  It boots to the desktop OK.

---

### Post by ju2wheels on 2008-12-27
The only problem I had with Alpha 2 was Nautilus crashing at the last install screen when choosing where to place the MBR.

---

### Post by vishalrao on 2008-12-27
This might be something Captain Obvious might say, but unless you're specifically targetting testing the installer, why not just install Alpha 1 or Intrepid and upgrade from there?

---

### Post by ju2wheels on 2008-12-28
I was running it in VirtualBox, not a dedicated system so its just easier for me to download the iso image and start from there. I did actually have Alpha 1 but it failed to successfully upgrade to Alpha 2 and I messed it up further doing other mods so I just downloaded the iso since I was curious at how progress is going.

I might eventually just use my Eee PC for dedicated testing the future at some point.

---

### Post by PRGUY85 on 2008-12-28
Does it look just like Intrepid at the moment or does it have any noticeable changes?

I am looking forward for the notification changes the team plans to add to Ubuntu but don't see them coming for this release.

---

### Post by jerrylamos on 2008-12-28
> **PRGUY85 said:**
> Does it look just like Intrepid at the moment or does it have any noticeable changes?

I am looking forward for the notification changes the team plans to add to Ubuntu but don't see them coming for this release.

Take a look at the Jaunty forums.  Quite a number of changes.  One I really appreciate is shutdown takes 13 seconds on Jaunty.  On Intrepid it takes about a minute, most of which just looking at a blank screen.

I haven't timed boot, however I think that's faster too.

You Tube video's are working well at the moment.  Much of early Jaunty sound was broken, I think the Pulse Audio people were trying something? which didn't work on one or another of my test systems depending on what they were trying.

Big thing that doesn't work is manual install.  Edit partition "use as" crashes every time.

Jerry

---

### Post by Gina on 2008-12-28
I have Jaunty working fine on my laptop from Alpha 1 with updates.  It was working similarly well on my AMD64 desktop until an update to xorg stopped the nvidia display from working.  I have had no joy with manual install of Alpha 2 either - same problem.  Sound has been fine on my systems so far.

---

### Post by PRGUY85 on 2008-12-28
I read something about new backgrounds already being included.  Is this true?

---

### Post by Gina on 2008-12-28
Haven't seen any.

---

### Post by Slug71 on 2008-12-28
I still have no sound into Alpha 2 even with the new 2.6.28-4 Kernel :(

---

### Post by knarf on 2008-12-28
X seems to be b0rked for now: the savage driver segfaults ([bug reported]("https://bugs.launchpad.net/bugs/311544")), the vesa driver has problems setting mtrrs, input devices are not recognized (symbol errors in mouse_drv, xf86OSMouseInit undefined). I'm debugging savage, the rest is up to somebody else...

EDIT: I made a small patch which fixes this segfault, it is attached to the bug report.

---

### Post by Gina on 2008-12-29
Yep, no display after bootup on my AMD64 with nvidia graphics and I'm not feeling up to sorting it out.  I installed Alpha 1 onto a new root partition but keeping the home, which worked fine (as expected, including installing nvidia 177 driver) so I tried an update in Synaptic (so I could see what was happening) 500 updates and it wanted to remove the nvidia driver, so I've left it for now, otherwise I'd end up just where I was - with no display!!  I know there's a problem with xorg update and my display won't work right with the nv driver.

---

### Post by vishalrao on 2008-12-29
nv worked for me, but i anyway got the 180.18 beta from nvidia and that works with the IgnoreABI option, this could work for you, im on amd64 too.

to sort it out, you could select the recovery grub item and drop to a root shell, then edit xorg.conf and use "vesa" to at least get X back :)

---

