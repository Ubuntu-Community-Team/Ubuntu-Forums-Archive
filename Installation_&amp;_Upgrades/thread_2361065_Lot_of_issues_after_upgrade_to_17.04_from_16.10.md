---
title: "Lot of issues after upgrade to 17.04 from 16.10"
date: 2017-05-11
forum: Installation &amp; Upgrades
---

### Post by vortex06 on 2017-05-11
1st had a very hard time with the install breaking. After multiple downloads did get it done but now boot is extremely slow & launching apps is also. Have had random issues with Firefox crashing and hard locks . I believe that is fixed after backing off tweaks to "about:config" that worked before  but now network is randomly slow?  Also am now getting this error message popping up after I log in and system goes to sleep and woken up but it is not consistent "GDBus.Error.org.freedesktop.DBus.Error.NoReply:Method call timed out" . Running on a Samsung NP-RV511 4gb mem 500gb hd Intel core 3
M 380 2.53ghz. Had no issues and was fast and stable with 16.04 & 16.10 has been a night mare since 17.04 upgrade Problems all started after first update for 17.04 . Had a issue with a header file locking, wouldn't install, couldn't delete or repair... Tried everything on forums to fix and it just got worse till point i thought i had a virus or malware. Had to format drive and install new. Then had issues with EFI and errors from Unetbootin. Thinking of going back to 16.10 or another flavour of Linux. Need stability for programming classes. Was so happy with system I deleted Windows 10 to just use Lubuntu  now I'm not sure:confused::confused:  Any one else having this many issues ? Suggestions ?? Thank you in advance !!

Mark

---

### Post by #&amp;thj^% on 2017-05-11
If I want a problem free Desktop for mission critical results...I would stay with the more stable LTS version's (Current 16.04 LTS)
Provided of course there are no hardware issue's

---

### Post by ian-weisser on 2017-05-11
> **vortex06 said:**
> 1st had a very hard time with the install breaking. After multiple downloads did get it done but now boot is extremely slow & launching apps is also. Have had random issues with Firefox crashing and hard locks . I believe that is fixed after backing off tweaks to "about:config" that worked before but now network is randomly slow? Also am now getting this error message popping up after I log in and system goes to sleep and woken up but it is not consistent

We need more details to be able to help you. Many more details.:

Are you saying that your 16.10 install was broken?
Or are you saying these problems began with the upgrade to 17.04?

Why did you need 'multiple downloads'?

Look at /var/log/syslog for the time around boot: What are the error messages or long delays between actions?

What *exactly* is the error message? If it's reporting a crash, then what does the appropriate /var/crash file say?

---

### Post by Dennis N on 2017-05-11
I think you should try a new install. I always do that instead of an in place upgrade. Lubuntu 17.04 is really quite good. In fact, I think it's the best release they have done.

---

### Post by Hagar Delest on 2017-05-13
On my machine, I've made several partitions and I keep especially 2 dedicated to the system: I use one for a version and when there is a new version, I install the new one on the other partition. And for the next version, I install on the first one and so on.
Thus, it's a brand new install each time and in case there is a problem I can keep running on the previous version.
It requires a bit of tunning since you also need a partition for your documents with symlinks so that you can retrieve all your places whatever the system is.
At each new version, you also have to reconfigure your desktop. But this way, you're sure to have a clean system.

---

