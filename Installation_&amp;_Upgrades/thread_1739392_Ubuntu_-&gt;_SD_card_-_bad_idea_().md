---
title: "Ubuntu -&gt; SD card - bad idea (?)"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2011-04-25
Have you ever used an SD card as a substitute for a hard drive?  I'm experimenting with that today, and it's not going very well.

The target machine is an MSI "nettop," more or less equivalent to a couple of netbooks glued together.  It has dual Atom CPUs, 2 GB RAM, an optical drive, and a bunch of other ports and connectors not usually found on netbooks but standard on a desktop machine (thus the "nettop" moniker).  So this is no powerhouse computer, but Ubuntu should run decently on it.

That's the thing: the machine has no hard drive.  Instead, it has an 8 GB SDHC card.  While the card is a "Class 10," and therefore well above average for an SD card, it's proving to be a poor substitute for a real hard drive.  I'm working on the machine for a friend, and I think I'm going to have to recommend he spring for a new SATA HDD.

Installing Ubuntu 10.04 from a CD-ROM to the SDHC card took forever.  At least there was ample space (just try cramming Windows 7 into 8 GB!).  Similarly, the first round of updates took almost all day to install.

The system is very sluggish in general, more so than is normal for a netbook-class machine, based on my experience with Ubuntu 10.04 on an Acer Aspire One D150.

I suspect that the basic problem is the glacial speed of the SDHC card compared to a SATA hard drive.  Although the SDHC card is rated for 20 MB/s reads, that's nowhere near even a slow SATA hard disk.  Write speed is likely a lot slower even than that, which perhaps explains the hours and hours required to install Ubuntu + updates.

It seems as if launching apps is slow as well - again, probably a symptom of the SDHC card's sluggish reads, compared to a SATA HDD.

Are there any secret tricks to make running Ubuntu off an SDHC card more bearable?  Or should I just tell my friend he needs to buy a regular HDD?

---

### Post by Hedgehog1 on 2011-04-26
I run several '**Ubuntu-On-A-Stick!**' USB installs.  The key to making them comfortable is (in large part) the fastest possible USB stick.

If this netbook was designed to use SD only as secondary storage, the interface to the SD card may not be very fast, either.

If you have a faster SD card you can use as a test, that might tell you more.  Many folks do use SD card based storage successfully, but everyones hardware is a little different.

I don't know if this helped...

***The Hedge***

:KS

---

### Post by Objekt on 2011-04-26
SD doesn't get any faster than Class 10 at the moment.

The card reader has a full "480 Mbit" USB 2.0 connection, which is good for less than that, realistically.  

Without a real hard drive - either SSD or mechanical - I know of nothing I can do to make the machine work faster than it does.

---

### Post by C.S.Cameron on 2011-04-26
I often boot my EEE PC from SD card.
It's a little slow.

I understand running Ubuntu in RAM is extremely fast but I have not got around to trying it yet.
Check it out:

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by Objekt on 2011-05-13
My friend decided to put an SSD in his nettop.  So that sucker is going to be SCREAMING fast when he's done with it.

A Class 10 SD card is still a Very Nice thing to have.

---

