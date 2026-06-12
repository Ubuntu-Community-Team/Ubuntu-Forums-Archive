---
title: "Startup inconsistent failure"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by dtrain on 2008-06-05
OK...I am a noob.  I recently installed Ubuntu (8.04) as a dual boot with XP.  I backed up everything and then wiped the whole drive and then created partitions using gparted.  All of that seems to work fine. I have two partitions for Ubuntu-one for the OS and another for the swap drive.

My problem - I suspect has something to do with video drivers or something like that, but I don't really know how to fix it.

Everything seems to work well-sometimes.  The problem is Ubuntu doesn't seem to consistently complete the boot.  From reading a little around forums, I think technically it is x-session that doesn't start up consistently.  I say that because even when it fails I get all the way to the nice graphical Ubuntu logo with the orange install meter across the bottom.  The meter sort of scrolls back and forth and then starts filling up.  It gets full and then it just go to nothing on the screen.  Right before it happens I see a tiny splash of orange across the bottom of the screen that looks like it is the login page.  Now the weird thing is that this doesn't happen consistently.  Sometimes it will boot up.  I tried enabling boot logging from reading another forum, but apparently that doesn't work in 8.04.  I reviewed the /var/log/messages of two different boots but don't see anything obvious. 

So, I tried several boots to see if I could give an idea of what is going on.  I shut down the machine after each boot.

BOOT 1  - NORMAL
BOOT 2  - NORMAL
BOOT 3  - FAIL
BOOT 4  - FAIL
BOOT 5  - NORMAL
BOOT 6  - FAIL

I don't even know what information to provide from logs.  Please help.

---

