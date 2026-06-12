---
title: "Newer version of Tomcat 5.5 available in 10.04?"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by Rapport12 on 2011-09-06
Hello all,

I've inherited an Ubuntu server that was managed by a previous administrator.  It's currently running version 8.04.4 LTS.  The current Tomcat version is 5.5.25, which has a handful of vulnerabilities.  I'd like to upgrade Tomcat to the latest version (5.5.33), but it would seem that version 5.5.25 is the latest version available in the repository.

If I upgrade the server to Ubuntu 10.04.3 LTS, is a newer version of Tomcat available, or do they use the same repository?  I understand that I could just download the latest version outside of apt, but I prefer the apt method as it sounds like the easiest.

Thanks so much!
William

---

### Post by mörgæs on 2011-09-07
Hi, welcome to the fora.

I recommend that you download 10.04.3 and try a live boot before doing the upgrade. During the live boot you can open Synaptic and see the version numbers for Tomcat and other packages.

---

### Post by Rapport12 on 2011-09-07
Good call!  I did that, and it looks like they offer Tomcat 6 in Ubuntu 10.04.  I am not quite ready to make the major version leap, so I'll stick around at 8.04 for a while and see if they release an update to Tomcat 5.5.33.  Ubuntu 8.04 LTS is still supported so I would expect that eventually they would.  Thanks for your help!

---

### Post by mörgæs on 2011-09-08
You are welcome. Please mark the thread 'solved'.

---

