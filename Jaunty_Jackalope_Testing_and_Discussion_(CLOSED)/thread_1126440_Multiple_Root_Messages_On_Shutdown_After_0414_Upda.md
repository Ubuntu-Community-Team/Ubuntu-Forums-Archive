---
title: "Multiple Root Messages On Shutdown After 04/14 Updates"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by SketchyClown on 2009-04-15
I always have the bootsplash's disabled because I prefer the verbose boot & shutdown.:)

After the updates on 04/14 I have noticed that when I select to restart the computer, I get multiple instances of: 

***"Broadcast message from root"***  (etc) [B]"The system is going down for *reboot* NOW!"

[/B]Enough instances that it fills the screen from top to bottom.

Before the updates it would only do this once like normal and then tell me it was shutting down ALSA etc, etc....

Its like its broadcasting to tons of users, but of course I am the only user on this system.

Anyone else notice this strange quirk after updating the other day?

---

### Post by zika on 2009-04-15
+1
I attributed that to my pushing concurrency=shell maybe too far, but now that You raised that question I do wonder ...

---

### Post by 4Orbs on 2009-04-15
Me too. Also, the "beep" at shutdown has doubled in length.

---

### Post by SketchyClown on 2009-04-17
This strange behaviour has not changed with the release of the RC. I suppose this is since the RC is the daily from the 14th according to the FTP sites. Got some updates today, but they have failed to fix this annoying issue. 

I'm going to switch my sounds back on to see if I am getting the extended beeping noises.

**EDIT:** turned sounds back on, no beeping here, but not using bootsplash either. Just a screen full of broadcasts from root that we're shutting down. All messages seem identical.

---

### Post by Darkshade on 2009-04-17
Same here, I noticed it a couple of hours ago when I was restarting but I was late for work (once again) and didn't have time to post about it.

---

### Post by tad1073 on 2009-04-17
Same here.

---

### Post by paradigm2 on 2009-04-17
+1

Noticed it from a remote ssh session.  At least five warnings all in rapid succession.  No big deal but somehthing is off...

---

### Post by SketchyClown on 2009-04-17
I have observed the same behaviour on shutdown as well as reboot.

Might be time to file my first bug.

**EDIT: **Report filed. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363154](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363154)

---

