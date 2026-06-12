---
title: "Installing less than 2G hard drive"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by RescuePenguin on 2011-01-23
[COLOR=RoyalBlue]Background:[/COLOR]

I have finally got a replacement keyboard for my EEE PC 701 and it is back up and running. I'm tired of the very functional Xandros on it. My plan is to put a stripped down newer version of Linux on it. My first choice is the netbook remix. I tried 10.10 and it demands a minimum of 2.3 G and the netbook has a 2G SSD in it.
I do have 10.04 netbook remix on my newer Acer netbook and love it. 

[COLOR=RoyalBlue]Question: [/COLOR]

Is there a way of getting 10.10 netbook remix on a drive 2G or smaller. When I tried the installation failed due to not enough room on the drive?
[COLOR=Black]


[/COLOR]

---

### Post by garvinrick4 on 2011-01-23
> **RescuePenguin said:**
> [COLOR=RoyalBlue]Background:[/COLOR]

I have finally got a replacement keyboard for my EEE PC 701 and it is back up and running. I'm tired of the very functional Xandros on it. My plan is to put a stripped down newer version of Linux on it. My first choice is the netbook remix. I tried 10.10 and it demands a minimum of 2.3 G and the netbook has a 2G SSD in it.
I do have 10.04 netbook remix on my newer Acer netbook and love it. 

[COLOR=RoyalBlue]Question: [/COLOR]

Is there a way of getting 10.10 netbook remix on a drive 2G or smaller. When I tried the installation failed due to not enough room on the drive?
[COLOR=Black]


[/COLOR] You know I am sitting looking at an old 2 gig flash drive with karmic on it made from Startup disk creator. Is using 1.8 gig of it. It was used as a live USB for karmic for me but has persistence so it is an actual system. Worth a thought to make with a live cd and using startupdisk creator and choosing the internal drive if it is possible. Never tried myself but a thought to look into.

---

### Post by RescuePenguin on 2011-01-23
It is relatively easy to install Linux on a small drive, it struck me as odd that the remix would state that I need 2.3G without giving me a chance to not install what I don't need. 

I carry my files on USB drives and micro SD cards on my person and not with my netbooks or laptop. That way if the computer is stolen my work isn't, it also allows me to use any computer I want at any time.

---

### Post by C.S.Cameron on 2011-01-23
What I did with my EEEPC was to install Ubuntu to a pendrive using UNetbootin, add a casper-rw file and then add "persistent" to the syslinux.cfg file.
I used dd to clone this to the EEEPC hard drive.

Startup Disk Creator from the Live CD should also work.

---

### Post by Alxl on 2011-01-23
How about Ubuntu 10.10 Minimal ?  
 Less than 1GB -  You can add only what you need.

[http://ubuntuforums.org/showthread.php?t=1673030](http://ubuntuforums.org/showthread.php?t=1673030)

---

### Post by snowpine on 2011-01-23
It is possible to install a stripped-down "barebones" Ubuntu using the minimal installer: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

However, I would recommend either A) purchase a 4gb or larger SD card, or B) use a lightweight distro such as Puppy or SliTaz.

---

