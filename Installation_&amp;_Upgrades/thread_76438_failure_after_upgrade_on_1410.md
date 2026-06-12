---
title: "failure after upgrade on 14/10"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by listen on 2005-10-15
Hi

i have been using Breezy for the past month and had been updating all relevant updates ....there had been minor errors but yesterday's one was the worse.
now i couldnt start X server.

more details of what happened:-
the computer stopped after loading for some time at some point and based on previous experience, i thought reset the power will be alright....(sometimes it does) after resetting there was an error msg saying problem with the file system and need to run fsck.....i ran fsck...and after typing a few 'y', rebooted the com...
now the comp always hangs at some point namely:-

Error: Temporary failure in name resolution
/etc/rcS.D/S55bootmisc.sh: line 24:
/var/run/utmp: Read-only file system
* starting system log daemon....    ...socket: Read-only file system

after some time a blue screen came up saying that it couldnt start X....and appear the prompt cursor for me to log it. Mentioned about checking syslog


FYI, i upgraded 2 files yesterday...cant remember what are their names...

what shall i do now? btw a newbie here.

regards

---

### Post by listen on 2005-10-18
reinstalled on the 16th after downloading the new official Breezy release.

realized that the system seemed slower when booting up.....will the development team take note please...i have been using Breezy for a month..and the preview is definitely faster during boot-up especially after keying in the userid and password..

anyway am writing to update my situation AND also report a bug here...

when i was using the preview:
during booting, with a "failed" in the clock synchronization, the system will still boot up...
but now, just now, i rebooted 3 times with the clock synchronization with utp.ubunt.com failure, followed by a temporary failure in name resolution and i get the exact same error in booting : 
/etc/rcS.d/S55bootmisc.sh line 24 /var/run/utmp: Read-only file system * starting system log daemon....     socket : Read-only filesystemmm

after sometime the screen will come up with a blue screen saying could not start X server...exactly the same problem b4 i reinstall....

what shall i do next??

---

### Post by mbwardle on 2005-10-18
You need to have a look in the X server log to find out what the problem was.  The log file is usually /var/log/Xorg.0.log.

Pay the most attention to any lines beginning with (EE) which indicate an error or any important looking messages at the end that might indicate a fatal error.

---

### Post by listen on 2005-10-18
Thanks

A look at that file gave me some warning lines regarding font renderer as follows:-

Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0

anyone pls?

---

### Post by listen on 2005-10-18
this is crazy....any superuser command with password keyed in will return an error msg:-

sudo: Cant open /var/run/sudo/mark/tty1: Read-only file system


what is wrong here?? 

actually there are many problems i never mention using Breeze...like doc files not opening, synaptic manager and terminal not opening ..got to reboot...

does hoary has the above problems? anyone? thanks

---

