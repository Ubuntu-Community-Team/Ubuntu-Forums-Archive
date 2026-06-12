---
title: "Cannot load hardware drivers"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Bieghe on 2007-10-30
I have been trying to install Gutsy, but when I use the live cd the progress bar just stops at a certain points and remains there.  I turned off the splash and quit parameters, and the last thing that I can read is "Loading hardware drivers" which is when it spits out a bunch of crap and just stops.  I was able to, however, install using the alternate CD, but when I try to boot into Ubuntu it freezes at the same spot.  
I have a HP Pavilion a814x, my computer specs are:
Intel Pentium 4 - 3.06 ghz
nVidia FX5500
1.5 gb RAM
and i am installing it on my secondary 160 gb hardrive.

Is there any way to tell which hardware it is having a conflict with, or is there some other fix to this problem?

---

### Post by ChrisBC on 2007-10-30
I'm having a similar problem with an HP machine of similar specs.  I actually had to do a fresh feisty install and then upgrade from there, because neither the Live CD or the Alternate CD would install.

Now, when I boot, it stalls at "Loading Hardware Drivers..." for a long time (read 2-3 minutes), and then it's 50/50 whether it will boot me into a BusyBox prompt (whatever the hell that is) or go to the login screen.

Any help would be appreciated.

Chris

---

### Post by dabl on 2007-10-30
> **Bieghe said:**
> 

the progress bar just stops at a certain points and remains there



This problem description frequently ends up being a "bad burn" of the CD image.  Make sure you burn the ISO at 4X speed, not faster.  Sometimes changing the brand of blank media makes a difference too.  Sometimes a different burner works better.


> 

I was able to, however, install using the alternate CD, but when I try to boot into Ubuntu it freezes at the same spot



This, on the other hand, is the classic "failed to autodetect the video card" problem.  Usually Alt-F1 or Ctrl-Alt-F1 will take you to the console, aka "text prompt" aka "CLI".  Here's how to deal with that (written for Kubuntu but the procedure is basically the same):

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

;-)

---

### Post by Bieghe on 2007-10-30
That did not work for me, when I hit Alt F1 it brings me to the same screen I would get if I turned off the splash and quit parameters on the live cd, and I am unable to type in anything.  The progress bar freezes almost right off the bat, it moves over about 1/10th of the way and just stops.

---

### Post by Bieghe on 2007-11-01
bump

---

### Post by mrblondeisback on 2007-11-01
I have the FX5500 and am experiencing the exact same problem.  I've never made it past the loading hardware drivers, and I can't ctrl alt F1 to the prompt it just locks up.  I'm working in another post (search posts by me) to figure it out but it seems to be a pretty common problem.  I think it is a fundamental issue with the kernel or something because I have Arch and that locks up at Loading uDev Events if I have the card installed as well.  I really hope we can find a solution soon, I want my investment in my video card to pay off.

---

### Post by Bieghe on 2007-11-06
I took out my 5500 and tried to boot and it loaded past the spot where it was previously stuck, however after that it had an error trying to start x server, so i know that my problem is the 5500.  Does anyone know a way for my 5500 to work?

---

### Post by aminesay on 2007-12-01
I'm having the same problem with pavilion t3000 with a fresh gusty install.
I have a wirless keyboard and mouse.When i switch to a standart ones i can at least use the prompt but i'm still having to wait at least Three Minutes for the 3loading hardware drivers" ... So if you have a cordless keyboard and mouse change them!!

---

