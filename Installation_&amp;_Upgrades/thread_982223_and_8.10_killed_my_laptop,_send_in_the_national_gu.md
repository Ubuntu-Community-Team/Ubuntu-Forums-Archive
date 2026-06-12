---
title: "and 8.10 killed my laptop, send in the national guard"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by djhvt on 2008-11-14
So i have a everex gbook (Via architechture) and it had been awhile since i updated my 8.04 so i thought it would be easier to just upgrade to 8.10, how wrong i was. I did this upgrade through the upgrade manager.

Now my laptop boots up, goes to the intial Ubuntu boot screen and then the screen goes white, the curser is in the middle of the screen and is blurry (and wont move)...and thats it. No log in, no nothing...it just sits at this white screen of doom forever.

So i pose the question, can it be fixed without loosing everything on my laptop? Or is there a way to undo the update and have my system work like it did before the update? I do have an 8.04 disk, but i wanted to check with this fine community to get a sense of what the best course of action would be.

Thanks so much in advance!:KS

---

### Post by jimv on 2008-11-14
Sounds like a video driver issues.  So we need to know what video card your laptop has.  To do that, boot into recovery mode (it's an option in the GRUB menu when you boot up) and run this command:

lspci | grep VGA

---

### Post by djhvt on 2008-11-14
ahh yes that pesky graphics card, it gave me some issues that were never solved under 8.04 as well...but they were tollerable. I have a VIA UniChrome9 HC IGP

---

### Post by caljohnsmith on 2008-11-14
Unfortunately, I don't believe there is any way of undoing the upgrade. One option you might consider is booting your 8.04 Live CD, open a file browser to access all your important files on your Ubuntu partition, back them up, and then simply do a fresh install of Intrepid. If the fresh install doesn't work, you can always reinstall Hardy. Or maybe you'll get lucky and find a cure for your current booting problem; if you want to go that route, you could look in your /var/logs directory in your Ubuntu partition and see if any of the logs contain clues about your problem. Anyway, just some ideaas. :)

---

### Post by DavMag on 2009-01-07
I have the same gbook computer you have witht he same problem, I was able to get a working update to 8.10 when I did it in Safe video mode. The downside to this is I only have 800X600 display right now and am work to change that. If I can't find the answers here on ubuntu's forums I'll try everex's forums next. Plus my wireless card isn't working either. If I find an answer I'll try to reply to your thread again, with any luck.

---

### Post by DavMag on 2009-01-08
I still haven't been able to get 8.10 to work entirely but 8.04 seems to work pretty darn well with my everex gbook. right now I'd think the best think to do is run it til, someone comes up with a solution. I'll continue to play with it, but so far I've only been able to get it to work with 800 by 600 display and the hardwired network card, under 8.10 everything but the sound works after the install of 8.04

---

