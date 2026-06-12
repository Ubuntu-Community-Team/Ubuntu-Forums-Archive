---
title: "Botched ubuntu ibex upgrade"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by funky_munky on 2008-10-31
I would like some help with a upgrade gone awry.  I tried upgrading my laptop which lost its wireless connection in the middle which trashed my install because it forgot to finish updating when update-manager was restarted it decided it needed to remove the packages rather than update them.  Well I learned my lesson don't try wireless upgrades.  Anyway here I am trying to upgrade my desktop and the update-manager just disappeared.  It changed my sources.list file to intrepid and lsb_release -a says intrepid but nothing got upgraded.  What do I do.  I restart the upgrade-manager and it does not say anything needs to be upgraded or updated.  I really don't feel like redoing my system from scratch again.  Please help me to figure out how I can save my system before a reboot is required.  It says I need to reboot but I am afraid to as I know it did very little downloading before it stopped.

---

### Post by anotherdisciple on 2008-10-31
try opening a terminal and typing:

```
sudo aptitude update
sudo aptitude upgrade
```

---

