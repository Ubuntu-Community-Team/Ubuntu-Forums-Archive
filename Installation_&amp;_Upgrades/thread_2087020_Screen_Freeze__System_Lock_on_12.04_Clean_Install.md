---
title: "Screen Freeze / System Lock on 12.04 Clean Install"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by manifestDensity on 2012-11-22
Ok, so this is a weird one.  I have been running Ubuntu since 10.04 or earlier, and while various upgrades have been eventful I always manage to get things going.  I'm running some fairly old hardware, so upgrades can sometimes be a challenge.  Probably the easiest upgrade was the move to 12.04.  That thing rocked straight out of the box.  I didn't have to make a single adjustment to my system.  It ran beautifully.  Unfortunately, I stupidly upgraded again to 12.10, which rendered my system unusable.  Long story short, I moved all of my data off of that drive, reformatted, and did a fresh install of 12.04.1 LTS.  This is exactly what I was running before my foolish upgrade attempt, and as I said, it worked perfectly. 

Now, however, same hardware, same everything, I'm having issues with the 12.04. Specifically, I get random screen freezes that come in two varieties.  One is the type that simply locks the screen ( no response from cursor, keyboard or mouse ) while freezing the screen at whatever was on there at the time.  Sometimes these last for about 30 seconds and then everything fires back up again.  Other times it is permanent and the only way out is to do a hard shut down.  This, obviously, loses everything I was working on at the time.  

The other type I get is a black screen.  More often than not the system recovers from this in about 30 seconds and soldiers on.  There have been instances, however, where the black screen also requires a hard shut down.  

In all cases there is no response whatsoever from keyboard or mouse.  I cannot short cut into a terminal or anything.  The frequency is several times per day.  There is no specific program or activity that is triggering them.  They happen at random times.  Overheating is not an issue.

Toshiba Satellite P205
2GB RAM
Intel 950 GMA 
Intel T2080 1.73GHz × 2 

Any ideas?

---

### Post by ramblinche81 on 2012-11-23
Mine is Toshiba A215 recently installed with 12.04 LTS off LiveCD. My system would not load completely and freeze during the pnpbios set up. Solved the problem by using nomodeset and pnpbios=off in the grub options start up. My limited understanding is the pnpbios sets up irq assignments.
 
My usb, hd, cd, wireless and ethernet and touchpad mouse are working with no apparent conflicts.
 
Not sure if it will work for you or not. From reading yours, it sounds like you can load, then later on the session you are freezing up which could be irq related. 
 
Good luck.

---

### Post by 2F4U on 2012-11-24
> One is the type that simply locks the screen ( no response from cursor,  keyboard or mouse ) while freezing the screen at whatever was on there  at the time.  Sometimes these last for about 30 seconds and then  everything fires back up again.

May be something is running in the background. You may find out by running a Task Manager.

> Other times it is permanent and the only way out is to do a hard shut  down.  This, obviously, loses everything I was working on at the time.

Looks like a crash. Did you take a look into the system log to see if anything has been logged that may give a hint on what is going on? Am I right in assuming that your system has all updates installed?

---

