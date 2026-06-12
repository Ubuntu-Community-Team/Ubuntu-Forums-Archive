---
title: "rpmdb: Program version 4.8 doesn't match environment version 4.7"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by jkuzenka on 2010-05-21
Hello All... I am a newbie to Ubuntu. I have Ubuntu 9.10 running on Dell Dimension 8400, 1 gig ram, Pentium 4. No other OS installed. 
 
Last night I decided to upgrade from 9.10 to 10.0.4 through Upgrade Manager with the upgrade button.
 
The upgrade ran over an hour and errored in the "Installing the upgrades" step with the following messages on the Terminal screen:
 
***"rpmdb: Program version 4.8 doesn't match environment version 4.7.***
***error: db4 error (-30971) from dbenv->open: DB_VERSION_MISMATCH: Database environmnet version mismatch***
***error: cannot open Packages index using db3 - (-30971)***
***RPM failed to open database, cleaning it up..."***
 
I went to bed without doing anything. This morning at 7:30am EST I checked the status of this and nothing changed to the screen it was still stuck on this error with progress bar at 4 minutes in Upgrade Manager.
 
I can move my mouse and even open Firefox 3.6.3 to search for issues within Ubuntu environment so I am not frozen. I haven't tried anything else yet.
 
Before I decide to do a clean install I was wondering if anyone knows how to get around this issue to try to complete the upgrade?
 
Any guidance is appreciated. Please review attached jpg print screen picture of this issue.
 
~Josh

---

### Post by jkuzenka on 2010-05-22
New Update.  I rebooted last night and was able to logon.  Ubuntu was upgraded to 10.04 even with the error.  I clicked on Update Manager again and it installed partial updates for where it had issues.

All set.  Wasn't a problem after all.:P

~Josh

---

### Post by hopfrog238 on 2010-06-10
I experienced this as well and found your message.  I was seconds away from rebooting when I happened to find a dialog window awaiting input (it was buried under windows I had open).  The dialog informed me about some RPM upgrade quirk.  After clicking "Forward", the upgrade continued.  I very nearly missed that dialog -- I'm guessing you probably had the same but missed it.

---

### Post by jkuzenka on 2010-06-10
[CENTER][COLOR=black][FONT=Verdana]>  hopfrog238[/FONT][/COLOR][/CENTER]
> 
 
**[COLOR=black][FONT=Verdana]Re: rpmdb: Program version 4.8 doesn't match environment version 4.7[/FONT][/COLOR]**
 
[COLOR=black][FONT=Verdana]I experienced this as well and found your message. I was seconds away from rebooting when I happened to find a dialog window awaiting input (it was buried under windows I had open). The dialog informed me about some RPM upgrade aoquirk. After clicking "Forward", the upgrade continued. I very nearly missed that dialog -- I'm guessing you probably had the same but missed it. [/FONT][/COLOR]
 
Thank you for sharing that you got the same error. I don't feel alone now in my experience with the upgrade from Ubuntu 9.10 to 10.04. I must of missed the dialog window as you mentioned. Luckly the rest of the upgrade went fine and the reboot seemed to work. 
 
My PC so far works perfectly without any other issues after running 10.04 for over 2 weeks now. I just bought a new wireless Lexmark printer and was able to install the print drivers printing to it wirelessly along with my other PCs on my home network. Also updated Virtual Box from 3.1.8 to 3.2.4 successfully last night. Ofcourse everything else like Firefox, update manager etc. has worked out of the box too.
 
I even tried Gwibber with my facebook account. Seems to work OK too. Not sure that I prefer it to logging on to Facebook and posting my comments yet.
 
:guitar:Have fun with 10.04.... 
 
Josh

---

