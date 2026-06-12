---
title: "Failed Gutsy Gibbon Upgrade &amp; No backup"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by diwhite on 2007-11-12
So, I used the update manager to upgrade from Feisty Fawn to Gutsy Gibbon.  Unfortunately, I didn't backup before the update, and now I'm a little SOL.  On reboot, I got some errors about the video card settings not being right, so XServer is going to be disabled.  Okay, that's not a big deal...I had to deal with that and fix that on my initial installation of Feisty Fawn.  So, as soon as I can get to the shell, I can work on that...

My problem, is that my computer stops loading after it tells me that it's disabling the XServer, goes back to the black screen, loads a couple of lines, and then does nothing.  I can't fix it if I can't get to the command line.  It isn't frozen, because if I press the power button, I goes through the shutdown sequence.  It just won't do anything.

So, I've accepted the fact that I'm probably screwed. It's kind of hard to do anything when your computer won't accept commands.  

I am now looking into an external hard drive, and a lot of them say things like, "embedded drivers for Windows & Mac" and I would like to know if it would still just automatically work with Ubuntu, through the USB drive.  

Also, any recommendations for a hard drive reader, or whatever they're called so that I can get my data off of the sata hard drive before doing a clean install?

---

### Post by luisromangz on 2007-11-12
First, have you tried the rescue mode? I mean, there should be an alternative boot entry in your grub menu, that should provide a root terminal, no X (unless you start it manually) and very few services.

Also, for the data backup, you can use a Live CD, for example Ubuntu's own, or Knoppix, etc.

---

### Post by gpilkay on 2007-11-12
I'd second that.  I'd take the Feisty CD (if that version worked well with your system) and use it and a USB stick to transfer your files (I keep at least a 2 gig on hand just for this sort of thing).  After transferring, you can wipe and re-load.  I'm updating next month, and I've already got everything set for a fresh install, just in case.  For any future update, while I know it sounds pessimistic, just look at it as though you will ALWAYS do a fresh install, and fi the on-line update works without a hitch, that's a nice bonus and you have some free time.

---

### Post by diwhite on 2007-11-13
Thank you!!  I did not know that the live cd could access the local file system.  Now everything is backed up and I can do whatever is neccessary to fix it.  

And then, if you want to talk about super weird....
I've restarted my system at least a half dozen times, and each time it did the exact same thing, just stalling after a certain point.  Well, last night I got a log-in prompt.  So, I'm not sure what my next step should be, if I even get a login prompt again.  

I love computers, I really do, but they always seem to do the weirdest things around me. Sometimes I just feel like I should give up my computer science degree and go build "modern art"

And about the rescue mode...even if that did work, I wouldn't know where to go from there, what files to look at and fix.  I can make my way around a working linux system...but trouble-shooting what is wrong?  Not so good about that.  

Thank you for your help!  I really appreciate it!

---

