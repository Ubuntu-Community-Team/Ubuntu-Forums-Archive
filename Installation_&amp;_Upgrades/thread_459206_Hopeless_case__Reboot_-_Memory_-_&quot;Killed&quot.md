---
title: "Hopeless case?  Reboot - Memory - &quot;Killed&quot;"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by VanceMac on 2007-05-30
I am wondering whether my case is just hopeless.  I have this old 98 machine, it is a strange Gateway "all-in-one" in which the computer is squeezed into the monitor base.  I figured it looks pretty cool and might be fun to use as an Xubuntu machine primarily for internet, which would actually be more useful and effective than 98 (which can't handle even a simple USB key).  It has only 64 mb of ram and a 500 mhz celeron processor.

The problem is that it can't complete the installation.  It could be a bad CD drive, but I tried it with other apps and it reads them fine.  At first, it did not even get to the opening page (where you choose "start or install", etc), and it would tell me the boot failed.  Now, it will get past there, and it will either fail loading the linux kernel, with an "error reading boot cd" message, or it will get past that and into the "cylon eye" loading page.  Then it will go black and give some error messages and some "OK" messages.

The errors are about insufficient memory, usually, and something about the process being "killed".  Something 

I have reburned a few different disks, but all with the same effect.  Oddly, if I go into Windows, and check the CD, it shows the files fine.  This machine is not connected to the internet now since I don't have a wireless adapter that works with 98.  If I can't get the CD to work, is there another option?  I have not been able to get a USB key to work either, but maybe with a driver on a floppy I could do that.

Any thoughts?

---

### Post by srt4play on 2007-05-30
You could try using the alternate install cd, but 64MB IMO is too little even for Xubuntu.  If it were me I'd go with a server install and then install fluxbox as the gui.

---

### Post by VanceMac on 2007-05-30
hmmm, I could check to see how hard it would be to add memory, but I wonder whether the type of memory it would use is even still readily available.   I have not tried to pop it open, but I am sure it is weird in there.  What amount would run Xubuntu smoothly do you think?

---

### Post by Yoooder on 2007-05-30
> **VanceMac said:**
> hmmm, I could check to see how hard it would be to add memory, but I wonder whether the type of memory it would use is even still readily available.   I have not tried to pop it open, but I am sure it is weird in there.  What amount would run Xubuntu smoothly do you think?

If it's a 98-era machine, chances are quite good that it will be using PC133 RAM, which is absolutely dirt-cheap and almost as prevalent as AOL CDs.

Here's my recommendation: Try and flash the BIOS to the latest available version, try and determine the maximum amount of memory it can use and load it with it.  I would say at least 256mb, but 512 should be safe and probably won't cost much extra.

---

### Post by VanceMac on 2007-05-30
Great, thanks, I bet I could scrounge some from a friend who keeps a "box o' junk" with such stuff in it.   Now, the problem will be how to get INTO this thing.  It is really strange.

---

