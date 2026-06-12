---
title: "E: Unable to correct dependencies - libc6"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by SirPecanGum on 2010-10-14
Installed 10.10 and then executed install updates, as automatically recommended but get this error:

The following packages have unmet dependencies.
 libc6 : Depends: libc-bin (= 2.12.1-0ubuntu6) but 2.12.1-0ubuntu7 is installed
 libc6-dev : Depends: libc6 (= 2.12.1-0ubuntu7) but 2.12.1-0ubuntu6 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


Am I the only one?

---

### Post by SirPecanGum on 2010-10-14
BTW, please note I have tried the usual methods to fix broken packages...

sudo apt-get:

-f install
clean
autoclean
update
upgrade
dist-upgrade
autoremove

Synaptic > edit > fix broken packages and deleted apt cache.

Can't think of anything else...

---

### Post by SirPecanGum on 2010-10-14
The solution for me was to reinstall the system leaving unchecked the option for 'download updates during install' - I did check the 'install codecs option. The initial post install update completed without error and all is good.

---

