---
title: "Upgrade to Lubuntu 14.04 breaks J-Pilot"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by Timothy Taylor on 2014-06-18
I have upgraded to Lubuntu 14.04 and cannot get J-Pilot to sync with my PDA.

This was working fine in my previous Ubuntu 10.04 system, but it seems that I also need the pilot-link package which is missing from the software centre now???

---

### Post by TheFu on 2014-06-18
So ... I haven't used jpilot in ... er ... 10 yrs, but software center doesn't display all the packages available.  Install synaptic and try that ... or use apt-get directly or aptitude ... 

Might need to look for a PPA - I dunno.
**sudo aptitude install jpilot** worked here. No PPA needed.

---

### Post by Timothy Taylor on 2014-06-20
Got it working.

The requirements listed on the [J-Pilot website]("http://www.jpilot.org/requirements.html") specify that **pilot-link** is installed. Unfortunately, [http://www.pilot-link.org/]("http://www.pilot-link.org/") no longer exists.  I managed to track down a copy on [SourceForge]("http://sourceforge.net/projects/pilot-link/").

This is a new version of J-Pilot in the 14.04 repository, which apparently requires users to be members of the **dialout** group.

---

