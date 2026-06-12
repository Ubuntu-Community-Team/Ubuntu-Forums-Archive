---
title: "text comes up at bootup not GUI"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by Morchoe on 2010-08-01
I have recently installed Ubuntu 10.04 and the splash screen does not automatically come up. The text screen comes up and I have to put in my name and password. I then enter (/ect/init.d/gdm restart) and the splash screen comes up. I guess I know enough about GNU/Linux to get myself into trouble. My wife freaks out when she sees the command prompt. Can anyone tell me how to fix this. Thanks

---

### Post by Doobie9 on 2010-08-03
Does the GUI start up (or try to) and exit with an error? Or does the computer boot directly to a command prompt no problem? 

In the first case, there is some issue with your x settings (which seems unlikely since it works when you start gdm again). In the latter case, the system is perfectly fine [except for scaring your wife;)] but it is simply not starting at the appropriate runlevel, or somehow gdm has been removed from its appropriate runlevel.

In which case you may want to look into adding gdm 'back' to your default runlevel or changing your default runlevel. 

[I haven't done this much in Ubuntu--only in Debian. If this if your case, I don't think it can be fixed as easily as in Debian. But this is just my bad experience with upstart speaking. I'd much rather someone with more experience with Ubuntu runlevels help you with this.]

So just post the output of the command runlevel; that might give us a lead.

---

