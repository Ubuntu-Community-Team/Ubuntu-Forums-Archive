---
title: "repairing upgrade : telinit u cause system to hang"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by qwill on 2013-10-25
I'm trying to rescue a 13.10 ubuntu server upgrade (from 12.04) which went bad. (Power interruptoin half way).
I was able to upgrade almost all packages; but the system hangs for some package (libc6, libselinux libsepol etc...)
I was able to track down the problem to some postinst scripts in the /var/lib/dpkg/info directory.
More precisely, it apperars that the command 'telinit u' witihn these scripts crash the system 
(Lost network connexion and console hangs - only a reset can revive the system).

Any idea on how to debug the telinit thing ?

Thanks, Qwill

---

