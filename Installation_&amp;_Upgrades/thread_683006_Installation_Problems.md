---
title: "Installation Problems"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by snakepliskin85 on 2008-01-30
Ok I have read through alot of post one here and from what I can see I haven't found one that shows step by step details for a linux noob of how to install 7.10 on a new hard drive with the 8800GT. Now realize I am a noob and it would be appreciated if I could have a detailed step by step please. Thank you for taking your time reading this and I really hope I can start using ubuntu soon. I consider myself high a fast learner and Im not dumb by any means around computers I just a completely new to linux and would like to see what all its about. Please help

---

### Post by wjp.reg on 2008-01-30
Not sure what complications you anticipate, but a fresh install with no other OS is as simple as inserting the Live CD and running it to confirm hardware compatability.  If semi-satisfied, proceed with the HDD installation - it's provided as a link on the ubuntu Live CD desktop.  Couldn't be easier.

cheers!

---

### Post by snakepliskin85 on 2008-01-30
well 7.10 doesnt have the drivers on the disk for the 8800GT so there for when I try to install it it as me to run in low res mode then it just goes to a DOS like screen

---

### Post by wjp.reg on 2008-01-30
> **snakepliskin85 said:**
> well 7.10 doesnt have the drivers on the disk for the 8800GT so there for when I try to install it it as me to run in low res mode then it just goes to a DOS like screen

Then use the Alternate Ubuntu Install CD which runs in text mode, then activate/download the restricted drivers for your video once it's up and running.

---

### Post by papatrpt89 on 2008-01-30
> **wjp.reg said:**
> Not sure what complications you anticipate, but a fresh install with no other OS is as simple as inserting the Live CD and running it to confirm hardware compatability.  If semi-satisfied, proceed with the HDD installation - it's provided as a link on the ubuntu Live CD desktop.  Couldn't be easier.

cheers!

True.  However, in the case of the 8800 GT, things are a little funky.  It is unsupported by the Ubuntu default drivers without tweaking, and Envy doesn't support it at all.  Tis quite the confusing issue.  I have moderate experience (I'm certainly not great at Linux, but acceptably decent) messing with graphics cards on Ubuntu.  I couldn't get the 8800GT to work properly on a machine that I helped build.  I DLed the latest driver, compiled what I needed to, and got it working for a few minutes(and boy were they glorious!).  The driver released by Nvidia for the 8800GT on linux isn't perfect yet, and Ubuntu doesn't support it well.  Possibly on Hardy?

All that said, I think what needs to happen is integrating the following directions into the directions that I gave on my other post ([http://ubuntuforums.org/showthread.php?p=4119312](http://ubuntuforums.org/showthread.php?p=4119312))


> **PmDematagoda said:**
> Allright, I am running out of ideas right now, try this:-
```
sudo rm /etc/init.d/nvidia-* 
``````
sudo nano /etc/default/linux-restricted-modules-common
```Then add this to the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nv_new"
```After that is done, rerun the installer, reconfigure the X-Server and try starting GDM again.

Good luck!

---

