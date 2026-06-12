---
title: "Unable to return from Screen blackout"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by theantidj on 2010-05-05
Hi folks,

I'm looking for some assistance. I tried a search of the forums, but didn't know exactly how to word my problem.

In a nutshell: If the computer goes to blank screen (set that way in screensaver settings) I can hit a key and get the unlock dialog.  However, if I walk away for longer and come back, I can't get the machine to wake up.  It is powered on, but nothing comes up on the screen.  I can't get other terminals by using ctrl-alt-FunctionKeys, either.  I CAN, though, ssh into the machine from my desktop computer, and that works normally.

Any ideas of what's going on?

Some background:  

I've installed 10.04 off of a live CD onto my Toshiba Satellite A45-S250 laptop.  I had originally tried upgrading from 9.10 on the machine, however it wouldn't boot after the upgrade.  The live CD also originally wouldn't work for me until I used a work around that involved adding "i915.modeset=0 xforcevesa" to the boot command line of the "Install Ubuntu" option of the live CD.  This caused the CD to install, and now the laptop works properly.

The computer boots normally now, but on shutdown, the screen does go all "squiggly" before turning off.  This doesn't interfere with the shut down or start up, though. 

Any help you can offer would be appreciated.  I can post whatever logs or such that would help, but would have to be told what is relevant here. 

I've been using ubuntu on and off on this laptop since sometime in 2005, and have never experienced an issue like this.

Thanks!

---

### Post by theantidj on 2010-05-05
Update:

The freeze happens even without the screen saver turned on.  

I disabled the screen saver, but if the machine sits idle for more than about 5 minutes, it appears to freeze. 

Can still ssh in. 

Any ideas

---

### Post by MaggiesDad on 2010-05-16
I have the same issue but have found that if I power up the machine and don't do anything for a while I end up blank and cannot get out of it. If I power up and then bring up an app (firefox or thunderbird) the screensaver works ok.  I have turned off the power save stuff and has not helped. This is was not an issue on the old load. My machine is a Dell desktop.

---

