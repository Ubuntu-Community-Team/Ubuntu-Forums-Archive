---
title: "Adept database lock due to wrong entry in sources.list"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by hvralpha on 2007-06-07
Have a really weird problem. Entered a new repository in adept which I copied partially. When I tried to updated adept said it had a problem. I looked in sources.list file and saw mirror was wrong (no d in deb). Fixed with Kate and tried again. 

Same problem. Tried dpkg --configure -a, removing lock files in /var, deleted sources.list and replaced with saved version, deleted all data in sources.list and replaced with newly generated  version. problem does not go away.

I think there must be an entry somewhere else in the system which registers the error and prevents it being fixed even though the sources.list is fixed.

Any ideas or suggestions?

---

### Post by hvralpha on 2007-06-07
Thanks eveybody.Got it sorted. There are 2 files in /etc/apt. sources.list and sources. I fixed sources.list but did not know I also had to fix sources. Fixed sources with kate and run dpkg --configure -a and voila!!

---

