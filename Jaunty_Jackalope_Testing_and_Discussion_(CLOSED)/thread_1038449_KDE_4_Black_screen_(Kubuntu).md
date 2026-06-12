---
title: "KDE 4 Black screen (Kubuntu)"
date: 2009-01-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by caryb on 2009-01-12
After todays upgrades I now have a lovely black screen & dozens of crash reports. I would hold off upgrading at the moment till the missing dependancy or rouge app is repaired. I will fill in a bug report as soon as I find something usefull in the logs.


Cary

& no I didn't dist-upgrade!

---

### Post by plun on 2009-01-12
Maybe sitting in the same boat as me...?

Install kerneloops for a check.

Dont "bomb" kerneloops with reports if it is so...

Apport also starts for a report to Launchpad.

---

### Post by dualscreenman on 2009-01-12
Wait until the rest of KDE 4.1.96 hits the mirrors, update, and everything should be fine.

---

### Post by Vorian on 2009-01-12
> **caryb said:**
> After todays upgrades I now have a lovely black screen & dozens of crash reports. I would hold off upgrading at the moment till the missing dependancy or rouge app is repaired. I will fill in a bug report as soon as I find something usefull in the logs.


Cary

& no I didn't dist-upgrade!
We are pushing through the 4.2RC, best to wait.

---

### Post by ruik on 2009-01-14
Hmm.. I did a clean Kubuntu install from today's daily build and installed all updates, but now I'm having a problem when logging in.. after entering username and password and logging in nothing happens. No splash screen or anything, it just stalls there. Where should I start digging or should I just wait for updates?

---

### Post by LordVeovis on 2009-01-14
can you get to a console? (ctrl-alt-f(2-6))

If so, it at least means it's not frozen

---

### Post by ruik on 2009-01-14
Yes I can, and I've already been reading some logs.. haven't found anything yet though.

I formatted the partition as ext4. Is there a way I can access it from 8.10? Would help reading the logs a bit. :)

---

### Post by LordVeovis on 2009-01-14
> **ruik said:**
> Yes I can, and I've already been reading some logs.. haven't found anything yet though.

I formatted the partition as ext4. Is there a way I can access it from 8.10? Would help reading the logs a bit. :)

Live boot a jaunty CD and use that to access the internal drives.

---

### Post by cdekter on 2009-01-14
I've had this same problem for about 3 days now. Just installed another 80Mb of updates this morning, still no dice - just black screen after login. I can get to a terminal (that's how I've been installing updates) using Ctrl + Alt + F2

---

### Post by ruik on 2009-01-14
Mine shows background image and mouse cursor though. It just doesn't go any further after the login box is gone (i.e. after entering username and password). I'll check all logs out tomorrow.

---

### Post by caryb on 2009-01-14
Mine is fixed as of 30 mins ago:guitar:


Cary

---

### Post by ruik on 2009-01-15
Installed today's updates but it still doesn't work..

```
Jan 15 13:24:46 agamemnon kdm_greet[3637]: Cannot open default user face
```

Possibly related to this?

---

### Post by tyk on 2009-01-16
My friend also seems to be having the same problem. Kubuntu 8.10 starts up but randomly black screens out. I know the comp is not frozen as conversation on skype is still going on, except the screen is blank. Earlier it was happening while exploring photos/videos in Dolphin. What gives? Are there new updates or fixes?
Caryb, how did you manage?
Thanks.

---

### Post by caryb on 2009-01-16
I had to install the Nvidia proprietary driver to fix my problem. I just rebuilt my laptop with the daily build cd 16/1/09 & I was amazed how many work arounds I performed 18 months ago are still there. Black screen, beeping on startup & upsplash missing/fails to work:confused:


Cary

---

