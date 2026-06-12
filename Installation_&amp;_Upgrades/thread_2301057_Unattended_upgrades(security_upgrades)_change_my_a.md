---
title: "Unattended upgrades(security upgrades) change my apache to prefork"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by Matous_Mojzis on 2015-10-30
Hello,
I use unattended upgardes for security upgrades and this is second time, that auto security upgrades change apache2_mpm_event to apache2_mpm_prefork, because of it install libapache2_mod_php5. Why does it install it? Is there any way to not to do this in future? It is really boring to change it on about 50 servers...

---

### Post by TheFu on 2015-10-30
If you have 50 servers, start using **ansible**.
**aptitude** can mark packages to not be removed - look at "safe-upgrade" "keep" and "hold" options. Should solve this.

Don't know anything about "unattended patching" - never trusted it. Been using a tiny script to run patches and log everything. Then I can review the log for all servers quickly with a few greps immediately.  If I'm not busy during the process, tail -f lets me watch the patch in real-time.

---

