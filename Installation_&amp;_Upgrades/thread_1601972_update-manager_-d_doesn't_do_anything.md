---
title: "update-manager -d doesn't do anything"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2010-10-20
I have several machines running Linux (approximately 15).  A couple I have managed to get updated to 10.10.  Most, if not all are on 10.04.  I try to keep them upgraded each new release of Ubuntu.

Over the past few days I've tried to get "gksu update-manager -d" to work to no avail.  Regular updates work.  I'm not told when I invoke that command and the update manager loads that I can upgrade to 10.10.  

Is there some issue with Canonical/Ubuntu in that they aren't permitting updates at this time?

---

### Post by NaiGuy on 2010-10-20
did you insure the update manager is set to check for all Upgrades and not just LTS versions?

---

### Post by arpanaut on 2010-10-20
To upgrade from Ubuntu 10.04 LTS on a desktop system, press Alt+F2 and  type in "update-manager -d" (without the quotes) into the command box.  Update Manager should open up and tell you: New distribution release  '10.10' is available. Click Upgrade and follow the on-screen  instructions.

You don't need the gksu, update manager will prompt you for password.
 I remember a post earlier this week that sudo or gksudo etc. screws up the process.

---

