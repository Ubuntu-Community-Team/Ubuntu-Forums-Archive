---
title: "I missed the removal step after my upgrade from Oneiric to Precise."
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by mhsafe on 2013-06-23
Hi  I have just upgraded my ubuntu form Oneiric to Precise. But unfortunately my PC hanged up, just before I was to start the removal step to remove the unnecessary packages.  Hence, after a restart my PC is working well but keeping the old and unnecessary packages is wasting my limited PC resources.  Please help me how to identify and remove them?   regards,

---

### Post by dino99 on 2013-06-23
from a terminal, after having booting to Precise, run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get -f install
sudo dpkg-reconfigure -phigh -a
(can take a while, be patient & dont stop it before it end itself)

you also can try to find/remove the orphan packages by installing & using gtkorphan & bleachbit

---

