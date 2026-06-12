---
title: "Power failure while upgrading to Hardy"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by cdoebbler on 2008-05-19
While upgarding my Sony Vaio laptop to Ubuntu Hardy from 7.10 I lost power (accidentally let the battery run out). I was more than 4 hours into upgrade, all files downloaded and they were being configured and loaded. 

When power reconnected I can login as user with password, but then the system hangs. Any idea what I need to do to get back to finishing upgrade or even pre-upgrade state of my system? 

Thanks for any advice.:confused:

---

### Post by cdoebbler on 2008-05-19
Tried 'sudo dpkg --configure -a && sudo apt-get -f install' (which was sugegsted on another linux list) and it got upgrade running again. Maybe this will help someone else.:)

---

