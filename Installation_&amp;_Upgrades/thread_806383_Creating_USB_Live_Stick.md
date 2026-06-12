---
title: "Creating USB Live Stick"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by otterbuff on 2008-05-24
Super Noob trying to create a LiveUSB stick to see how Ubuntu will run on an old Dell Latitude LS.  Currently I am running Ubuntu 8.04 on VMWare Fusion on a Mac.  

I am attempting to follow the directions provided at:
[https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html)
However, I am stuck at the very first part - 'extract it directly to a partition on your USB stick.'  I can get to terminal and even get root access, however, if I put the text:
# zcat boot.img.gz > /dev/sda1
I get no where.  If I try to open it, it wants to know what app to use to open it.  My USB stick is: 
/dev/sdb1 and is called /media/USB

I am clueless where to go from here. I really want to learn, but I don't even know where to start.  

TIA

---

### Post by Herman on 2008-05-24
Here's a link, [How to install ubuntu on USB drive and carry entire computing system in pocket? ]("http://ubuntuforums.org/showthread.php?t=789528")

I think that you are being unneccessarily hard on yourself trying to take on an advanced how-to like that when you are not so experienced with Linux commands.
It would be much simpler for you to just install Ubuntu to your USB flash memory the simple way, as if it was just another hard disk.

Here's another, (more recent) link on the same subject,                           [Installing Ubuntu on a USB stick ?]("http://ubuntuforums.org/showthread.php?t=805596").
As you will see if you read those threads, there are some concerns that if the flash memory runs an operating system for long enough, there's a possibilty of wearing out the flash memory, but so far no-one has any idea how long that might take. Maybe 1 year? Maybe 100 years?
For a new user who just wants to try out Ubuntu I don't think it will be a problem.

Regards, Herman :)

---

### Post by SR_ELPIRATA on 2009-04-20
I have Ubuntu 8.10 installed on a 8gig pendrive, and it works great. Of course, performance is dependent on the hardware is running in, for example, it doesnt load as fast in a Sempron 2400+ with 768MB RAM compared to my current Amd64x2 7750 with 2gigs RAM, but it runs.

One thing that you'll note is that if you install the ati or nvidia driver (whichever you may use for the desktop effects) if you put the pendrive in another computer, it will boot up, but it will inform you of the hardware change and gives you instructions on what to do with it.

I find it very useful to have this option working, which I also tested on 2 Dell laptops (X1 and 600M) and in both it detected the wireless card and as you work with wireless routers it saves that data and no matter which laptop you used, you can access those routers and all that, its pretty cool.

ELP

---

