---
title: "failed to thaw from Intrepid"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by wahoobob on 2008-11-10
After a clean install of 8.10 I am getting a strange message whenever I try to suspend or hibernate.  the thinkpad T42p beeps and the message says:

pm-op(): pci_pm_thaw+0x0/0x50 returns -16
PM device 0000:00:00.0 failed to thaw: error -16

also sometimes the message says something about failed to resubmit.  This is worrisome, but the hibernation or suspend usually works.  I am just wary of using it if the information might be lost or corrupted.  Any ideas out there?:confused:

---

### Post by prangija on 2008-11-11
I've got exactly the same problem as you. Did you find any solution??

---

### Post by hcorey on 2008-11-12
Exact same problem after upgrade from Hardy, except in my case restore from hibernation almost always fails.

---

### Post by bomanizer on 2008-12-15
I get this too + sometimes the machine fails to hibernate and the sceen is filled with messages about something with swap & pages... I'm trying to find a log entry, but I can't find where hibernate puts the log entrys. Is there a place for hibernate/resume logging? Is it enabled by default? If someone could help me with logging, then I could try and recreate the error + post the logs.

I'm on a thinkpad R50.

---

### Post by Rogbert on 2008-12-26
Me three.  IBM X31, all else on 8.10 seems to be working great, but does seem to take a while to hibernate and resume.

---

### Post by ProteinPappa on 2009-02-05
I also get this. I got hibernation working after a great deal of trouble in hardy, but in intrepid it has never worked. On hibernating I get the message about not being able to "thaw" device 0000x000 (only zeros and an x), it does then shut down as usual. When I restart again it loads the image fine, but halts at the message saying it failed to resume said device. I have to make a hard restart (reisub doesn't work) which usually results in some kind of data corruption. Oh, it says something about pm.op() and error -16.

If anyone has any clue of what is wrong I'd be grateful to get this sorted out. My machine is an old P4 on an Abit A17 motherboard.

---

### Post by bomanizer on 2009-02-15
Bump. Any news?

---

### Post by bomanizer on 2009-02-15
Hey guys, there are some instructions to blacklist modules intel_agp and agpgart, but that removes 3d accel. support, at least for me. I'm using the radeon driver. Have you tried this? What's the outcome?

---

### Post by ProteinPappa on 2009-02-15
Thanks for the tip. For me it didn't make any difference, I'm using the propietary nvidia driver.

It's still in /etc/default/linux-restricted-modules-common I add the modules to be blacklisted, right?

---

### Post by bomanizer on 2009-02-19
> **ProteinPappa said:**
> Thanks for the tip. For me it didn't make any difference, I'm using the propietary nvidia driver.

It's still in /etc/default/linux-restricted-modules-common I add the modules to be blacklisted, right?

I think so.

I removed the modules from the blacklist, because I like my fps :) I then upgraded the pm-utils package just for the hell of it (from jaunty repos). I still get the error messages (failed to thaw, blaa blaa), but this seems to have fixed the issue where I would get a screen full of messages when hibernating. That caused the hibernate to fail, it happened after a few hibernate-resume- cycles. I tested this by doing many hibernate and suspend cycles in a random manner, no problems so far :)

BTW, I didn't touch my sources.list, I just downloaded the .deb for pm-utils from [here]("http://packages.ubuntu.com/jaunty/pm-utils").

---

### Post by ProteinPappa on 2009-02-23
Thanks again for the new tip. I still don't see any change.

Something I've noted, though, is after I restart and the regular loading happens, the error message appears and the screen appears to be locked. However, the disk is working for 20-30 seconds. I cannot use ctrl-alt Fx or anything, but I have a suspicion that it would be possible to ignore the error.

Also, what could they have done to the intrepid release that caused hibernation on some machines to stop working?

---

