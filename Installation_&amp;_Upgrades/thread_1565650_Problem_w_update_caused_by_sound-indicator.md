---
title: "Problem w/ update caused by sound-indicator"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by zoso375 on 2010-09-01
Unresolved dependencies showing when trying to run update-manager.  Synaptic and and apt-get update also broken.  Update-manager is showing packages as held back (unspecified).  Apt-get update shows the offending package as indicator-sound

```
indicator-sound: Depends: libdbusmenu-glib1 (>= 0.3.3) but 0.2.9-0ubuntu3.1 is to be installed
                   Depends: libdbusmenu-gtk1 (>= 0.3.3) but 0.2.9-0ubuntu3.1 is to be installed

```

Running Synaptic shows 0.2.9 as the latest available.  Any suggestions?  I'm stumped (or just outta my league).

---

