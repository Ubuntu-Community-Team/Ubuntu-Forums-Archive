---
title: "Katapult"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by utkjamie on 2008-11-02
I'm having problems launching just about anything with Katapult after upgrading to Intreprid. Just about any time I try to launch something with Katapult I get an error similar to:

> KDEInit could not launch /usr/lib/kde4/bin/...Apparently Katapult assumes everything is located in /usr/lib/kde4/bin, which is obviously not the case for most applications.

Any suggestions for fixing this?

UPDATE: Kubuntu 8.10 is not finding the correct location of kdesu (same problem as above), which creates a lot of issues for obvious reasons.

---

### Post by utkjamie on 2008-11-03
Am I the only person having problems with KDE4 thinking every app is in /usr/lib/kde4/bin/? This is affecting at least Katapult and, more importantly, kdesu.

---

### Post by MickS on 2008-11-03
I had the same problem with Ksnapshot, when I put it on my panel it wouldn't launch, gave me the same or similar error.  Fixed it by putting it on my panel then right clicking on the Icon and going to Icon settings, then to application and in the command box wrote ksnapshot instead of what was there and now it works as it should. I have no idea if Katapult works the same but it is worth a try.

Mick

---

### Post by ee19921 on 2008-11-04
I have the same problem. It seems Katapult is not ported for KDE4. You can use krunner instead (alt+f2).

[http://ubuntuforums.org/showthread.php?t=951983](http://ubuntuforums.org/showthread.php?t=951983)

---

### Post by utkjamie on 2008-11-04
Thanks for the info. Doesn't look like it supports Firefox bookmarks or Amarok music yet, but it still seems to do a good job for most everything I need it for.

---

### Post by ee19921 on 2008-11-04
> **utkjamie said:**
> Thanks for the info. Doesn't look like it supports Firefox bookmarks or Amarok music yet, but it still seems to do a good job for most everything I need it for.

no problem! Though this sort of works, I would like to see Katapult in action. :)

---

