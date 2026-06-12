---
title: "Installing 11.04 on Gateway 400vtx"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by ChrisBarthol on 2011-04-30
Hey Everyone,

I have an old Gateway 400vtx which i'm trying to installing 11.04 on.  I'm getting some really weird errors though.

I've burned an image onto a CD using infraRecorder at the lowest write speed possible to avoid write errors, and after running the check there are no errors on the cd.  When I try to install on the computer I get an error saying to the effect of "Unknown installation error, will load a desktop environment so you can try again".  Not the exact words, but something like that.

It then tries to load the 'try me' version from the CD.  It almost completely loads and then the screen goes black and looks like it is trying to reload the desktop.  It then prompts me for a username and password.  I'm able to log in with username:ubuntu and a blank password.  It then tries to load the desktop but 'reboots' when it gets close to the end and the cycle continues.

If I try to immediately load the desktop from the first options menu, I'm immediately put into the endless cycle.  Any ideas?

*UPDATE*
I've continued to mess around and have found that i'm able to mess around with the system settings when I receive the error message.  I've gone to the disk utility part and run a self check on the hard drive.  It says it is ok, but I do not hear it spinning up nor does the hard drive light on the computer go on.  It could be that the hard drive is dead, however ubuntu still thinks it is ok.

---

### Post by Hedgehog1 on 2011-04-30
Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

Run the Disk Utility and check the SMART status of the hard drive.  This will tell us if the drive is acting up, or if it is a different issue.

Thanks.

***The Hedge***

:KS

---

