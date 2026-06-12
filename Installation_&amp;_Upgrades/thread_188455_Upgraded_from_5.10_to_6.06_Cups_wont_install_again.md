---
title: "Upgraded from 5.10 to 6.06: Cups wont install again"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by TTL on 2006-06-04
Hello,
I just upgraded from Kubuntu 5.10 to 6.06. Unfortunately cupsys fails to install again: ** apt-get install cupsys ** results in:
```

Richte cupsys ein (1.2.0-0ubuntu5) ...
 * Starting Common Unix Printing System: cupsd    
cupsd: Child exited on signal 15!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: Fehler beim Bearbeiten von cupsys (--configure):
 Unterprozess post-installation script gab den Fehlerwert 3 zurück
Fehler traten auf beim Bearbeiten von:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Has anyone a solution, or know more about this problem?
Soon or later I will need to print someting...

Thank you in advanced.

---

### Post by TTL on 2006-06-04
For some unknown reason after an other ** apt-get upgrade** cups was configured fine... :)

---

### Post by Cavalierski on 2006-06-04
Delete the one you have already set up, and again make the printer setting. Then my Epson Photo915 works fine. 
```
sudo gnome-cups-manager
```
And delete one you have alredy set up, and make one again.

---

### Post by sedona on 2006-08-17
What if sudo gnome-cups-manager
responds with Command Not Found?

---

