---
title: "update manager not showing upgrade option"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2012-04-15
Running 10.10.  If I go to System>Administration>update manager sometimes it will show that an upgrade (to 11.10) is available.  Now that I am ready to do so, this message is no longer present.  Is there a way to have update manager handle the upgrade so that I do not have to download the .iso, burn the DVD, etc.?

---

### Post by raymondvillain on 2012-04-15
Solved.

sudo apt-get remove update-manager
sudo apt-get install update-manager

and then re-boot.

---

