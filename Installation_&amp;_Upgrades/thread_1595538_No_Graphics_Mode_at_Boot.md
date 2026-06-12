---
title: "No Graphics Mode at Boot"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by vchapman on 2010-10-13
I have upgraded from 10.04 to 10.10. The first upgrade failed. The second attempt worked, partially. Now when I boot ubuntu (dual boot xp and ubuntu) I get a brief flash of the splash screen and then the system drops into tty mode and asks for a login.
 
How do I restore the graphics mode at boot? Thank you.

---

### Post by VMC on 2010-10-13
> **vchapman said:**
> I have upgraded from 10.04 to 10.10. The first upgrade failed. The second attempt worked, partially. Now when I boot ubuntu (dual boot xp and ubuntu) I get a brief flash of the splash screen and then the system drops into tty mode and asks for a login.
 
How do I restore the graphics mode at boot? Thank you.

First try logging in, then type "startx" from the prompt, and see if it gets you to the Desktop. If so we then need your video hardware - nvidia, intel, ati, etc

---

### Post by vchapman on 2010-10-13
> **VMC said:**
> First try logging in, then type "startx" from the prompt, and see if it gets you to the Desktop. If so we then need your video hardware - nvidia, intel, ati, etc

This produces a whole bunch of errors!t

Fatal error: no screens found

It seems to be having trouble finding and loading the nvidia drivers

The system will run in safe mode with graphics, however, the screen resolution is wrong and the nvidia drivers do no get loaded

I know the nvidia drivers are there somewhere!

Let me know what else I can provide. Thanks for your help

---

### Post by VMC on 2010-10-13
Please read this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974") and see if your nvidia card is listed.

---

### Post by vchapman on 2010-10-13
> **VMC said:**
> Please read this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974") and see if your nvidia card is listed.

Yes, the graphics card is a GeForce MX420. The driver is nvidia-96.

Just as an aside, the live cd of ubuntu 10.10 runs ok on my machine. It manages the full 1920 x 1280 resolution without a problem. It identifies my Dell monitor, but does not use the nvidia drivers.

---

### Post by vchapman on 2010-10-13
Well I read some of the other posts on this topic -- seems to be very common.

I did this

sudo rm /etc/X11/xorg.conf

Now my machine boots ok with the correct resolution. Navidia is no longer in play.

---

