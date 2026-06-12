---
title: "unwanted network manager update"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by helicase on 2010-10-15
Since upgrading to maverick update manager keeps telling me I can update network manager (and a few depending packages) when I don't even have it installed. Any ideas what could be going on here (or what I could do to find out)? I'm 100% up to date otherwise and update manager seems to be the only program to offer this unwanted update (no mention of it in apt, for instance).

---

### Post by dino99 on 2010-10-15
maybe some outdated settings left behind, so its time to clean the system:
 the usual "clean, autoclean, autoremove"
and: gconf-cleaner (yes to all)
and: bleachbit: admin mode, set carefully the settings

sudo dpkg --configure -a

maybe some usefull errors logged too

---

### Post by helicase on 2010-10-15
Thanks for the tips. They didn't fix the problem, but I think I've figured it out now. It looks like network manager is a dependency of the ubuntu-desktop package. So it's either uninstalling ubuntu-desktop (can I safely do that?) or installing network manager (and abandoning wicd, because having both installed kills wireless).

---

