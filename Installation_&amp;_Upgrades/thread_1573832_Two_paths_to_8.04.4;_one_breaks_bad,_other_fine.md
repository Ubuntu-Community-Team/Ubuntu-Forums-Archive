---
title: "Two paths to 8.04.4; one breaks bad, other fine"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by buggyruss on 2010-09-13
I installed 8.04 Xubuntu from a 2008 CD I made since later versions of Ubuntu consistently freeze my old 600MHz PIII computer (the freezes are total - no ability to telnet in, no log entries, etc - these type of freezes are posted about by many many people here and elsewhere w.r.t. to later versions of Ubuntu (my most recent fruitlessly unsuccessful attempt was with 10.04 Lubuntu)).

Anyway, after successfully installing the above I decided to try to install 8.04.4 Ubuntu, also from a CD just created from the ISO file distributed. That installation came up but froze solid pretty much as soon as I started up Firefox. Same symptom as all the other later-release attempts - bring up (XL)Ubuntu and all works "fine" (*) INCLUDING network accesses until a browser is started, then total freeze requiring hard reboot.

I reinstalled 8.04 Xubuntu and allowed Update Manager to update it extensively. When it was done it was 8.04.4 Xubuntu and is working just fine still - no freezes of the system, no problems at all (yet!).

Anyway - that was essentially two different routes into 8.04.4, one that works, one that's broken. It could be the difference in window managers between Xubuntu and Ubuntu (that's just strange) or something even less obvious.

Just a datapoint for those out there trying to figure out what Ubuntu to keep...

=========

(*) It is important to note that the later-release PERFORMANCE was way worse than Xubuntu 8.04.4 - playing "freecell", for example, the cards move quite fast even with other main screen processes running - the later-release graphics are much slower.

W.r.t. performance as an aside - I stopped as much power-saving processes as possible (this is a plugged-in-the-wall desktop, afterall), the NetworkManager, bluetooth, etc, and saw an increment in performance even over its already-satisfactory performance.

Wish I knew how to turn off gnome-power-manager - under Xubuntu this is not apparent (can twiddle it a bit, but not obviously disable it totally).

---

### Post by snowpine on 2010-09-13
Curious if you thought to check the Ubuntu/Xubuntu hardware requirements before your experiment?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Without knowing more specifics of your hardware (RAM in particular; 1GB is the recommended minimum), I am tempted to say Ubuntu is crashing because your hardware is not up to the task.

---

### Post by buggyruss on 2010-09-13
Lest this go off on an irrelevant tangent, my hardware is just fine, albeit slow with the higher Ubuntu installs - that's why I've stopped as many of the totally-unnecessary processes that are running by default; still need to stop gnome-power-manager - haven't got that one figured out yet. Just killed off avahi a couple minutes ago, as one example.

The crashes, however, have nothing to do with processor speed (this system has had a gigabyte of RAM for years).

---

### Post by mörgæs on 2010-09-13
Rather than removing processes from a full *buntu setup I would go for a minimal installation:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by buggyruss on 2010-09-13
Thanks for that thread link - I'll read it (note, however, that my current Xubuntu install IS pretty minimal w.r.t. running processes since I've manually stopped/disabled almost all the not-really-necessary cruft).

But this thread wasn't about slow Ubuntu installs, it was about two similar installs, one that worked, one that didn't!

BTW - here's a thread that discusses what others have experienced with freezes:

[http://ubuntuforums.org/showthread.php?t=1469650](http://ubuntuforums.org/showthread.php?t=1469650)

Googling for "Ubuntu freeze" (or "lockup") turns up many many more around the 'Net.

---

