---
title: "Updating Nvidia drivers.. non-legacy to legacy"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by baconstrip on 2007-04-10
Hello everyone!  I am a very very new Linux and Ubuntu Edgy user and I have been learning a ton of stuff.  It has really been a blast figuring all this out, and I am finally feeling like I have a good grasp on the way things work.

It took me a very long time to get my nvidia drivers installed, along with multiple ubuntu reinstalls (oops.. forgot to backup xorg.conf!)

Currently I am running a Geforce 4 420 go with the 8776 non-legacy drivers.   I finally got Beryl0.2.0 up and running last night!   I am still having a bunch of errors when I boot beryl-manager... and after the initial run of Beryl, rebooting and re-running Beryl leaves me with a few problems.    But I will leave those for the Beryl forums.

One of the things that I figure I should probably do is update to the latest nvidia drivers and reinstall beryl, seeing if it makes the errors go away.   Considering that the Geforce 4 420 go is now unsupported by the main drivers, the most updated driver to utilize is the legacy 9631 driver.

I have found this Howto that deals with updating your nvidia driver to the latest version. 

[http://www.albertomilone.com/driver_edgy.html](http://www.albertomilone.com/driver_edgy.html)

My question is.... would following the steps in this HOWTO mess my system up, considering that I will be going from Non-Legacy drivers to Legacy drivers?    I have broken my install multiple times messing with nvidia drivers, and the prospect of having to redo everything again is not something I want to do! 

EDIT: Oh yes, one of the reasons I would like to update instead of completely uninstalling the Nvidia drivers is because I would like to keep my Xorg.conf intact. I had to add a bunch of lines and searching for the proper stuff might be a pain in the butt.  I suppose I could just back it up though and copy\paste if need be!  Still curious as to if I can just upgrade the drivers or not...

Thank you for your help, in advance :)

---

### Post by bulldog on 2007-04-10
I should un-install your current driver,and install the legacy.

Reinstalling ubuntu is the last thing you should do when you have messed up your install.
Try to solve the problems,or ask help on the forums,you learn the most of it.

---

### Post by baconstrip on 2007-04-10
> **bulldog said:**
> I should un-install your current driver,and install the legacy.

Reinstalling ubuntu is the last thing you should do when you have messed up your install.
Try to solve the problems,or ask help on the forums,you learn the most of it.

Yes, a good point.  That is my current plan from now on, now that I have a good grasp of how things work.

Question though, will uninstalling the current driver mess with all the lines I have added to my xorg.conf?

---

### Post by bulldog on 2007-04-10
If you want to keep your current xorg.conf for later reference,just make a copy of it.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by baconstrip on 2007-04-10
Thanks for your help!

---

