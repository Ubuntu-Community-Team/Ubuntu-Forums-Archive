---
title: "Cannot boot after hardy upgrade"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by fizban9 on 2008-05-29
I just ran the Hardy Heron upgrade on my Gutsy Gibbon  box and, after it finished, it rebooted.  Some of the normal stuff appeared, then, right after it says it's loading the hardware drivers, it gives the following error:

57.513176   intel_rng: FWH not detected

Then it sits there.  I can't even reboot, I have to do a hard shut down,  Eve n after that, if I try to bring it up too quickly it doesn't boot at all.  I have to leave it off for a few minutes first.

Please help me, I was just about to hack my new AppleTV to run ubuntu and now I can't do anything.

---

### Post by wpshooter on 2008-05-29
Can you, did you try going into recovery mode ?

---

### Post by fizban9 on 2008-05-29
> **wpshooter said:**
> Can you, did you try going into recovery mode ?

I can, and it gets farther in the boot process.  It gets past "loading hardware drivers" but after it loads my wireless driver (Broadcom 4301 WLAN found) it freezes there.  Can't hit enter, can't switch screens, nothing.
 
The only option I can choose that boots is the 2.6.22-14  kernel, but it doesn't have my graphics set up (dual  screen) and the resolution is way low.

---

### Post by fizban9 on 2008-05-29
Some more news, I looked up what the intel_rng thing is and it's a random number generator. I read that you can add it to you blacklist so it doesn't load.  I did that.  Now I don't get that error but it still justs sits there after it says "loading hardware drivers"

---

### Post by fizban9 on 2008-05-30
I got it working.  I snooped around the forums some more and saw that alot of people were having problems with the wireless adapter so I took mine out (I don't use it anymore anyways) and it worked fine.

---

### Post by trey.cecil on 2008-05-30
I too am having problems after a Hardy upgrade.  I did the normal upgrades and restart, but afterwards, my wireless driver and internal adapter no longer work.  I think I have an Atheros something wireless card.  Also, I no longer have sounds.  I get a message that says something along the lines of Gstreamer driver not installed and then my sound card is not set up.  I know it is because it was working before the upgrade.  Any ideas?

---

