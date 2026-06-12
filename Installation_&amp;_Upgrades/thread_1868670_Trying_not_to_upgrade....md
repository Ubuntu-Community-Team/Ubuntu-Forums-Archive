---
title: "Trying not to upgrade..."
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by chkl on 2011-10-24
I have this odd problem: I decided I might give 11.10 a try (from 11.04 desktop) but cancelled the version upgrade just before it would start downloading all new packets.
After that, trying to do a "normal" 11.04 upgrade, both the graphical upgrade manger and "sudo apt-get upgrade" insists on doing a version upgrade, trying to download 1000+ new files. I have tried the obvious (?) things like apt-get purge/clean/autoclean with no effect.

How do I reset the upgrade system to start doing normal upgrades and not to try to install the new 11.10 version ?
Is there something (some file) that should be deleted or edited ?

---

### Post by tudor117 on 2011-10-24
Check the sources.list (/etc/apt/sources.list).
You can use Software Sources Manager (not sure if you can find it in Unity...)

---

### Post by chkl on 2011-10-24
Thanks - commented out all lines in sources.list containing "oneiric". After that, update works OK.

---

