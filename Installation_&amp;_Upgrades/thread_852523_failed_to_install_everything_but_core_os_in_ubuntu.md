---
title: "failed to install everything but core os in ubuntu studio 8.04 installation"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by lnlog on 2008-07-07
I accidentally just installed the core install of Ubuntu that comes with Ubuntu Studio 8.04 by hitting the return key instead of selecting the correct software options. The install is fine, but my knowledge of unix is shaky at best, and I can't figure out how to just install the desktop environment/apps/etc off the install disk, or if that's even possible.

Any and all help appreciated! The install of Ubuntu successfully dualboots with XP... it's just, you know, missing everything. :|

---

### Post by Partyboi2 on 2008-07-07
Since its a new install have you considered reinstalling?

If you have a working connection to the internet you could at a terminal (Ctrl+Alt+F2) download and install these packages.
```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

---

