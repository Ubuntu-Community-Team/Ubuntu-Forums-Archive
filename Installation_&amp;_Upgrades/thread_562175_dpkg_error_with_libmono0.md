---
title: "dpkg error with libmono0"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by Raven404 on 2007-09-28
Here is the error:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 21737 package `libmono0':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

Stuck in a loop trying to run apt-get upgrade.

---

### Post by Pumalite on 2007-09-28
Did you run: sudo dpkg --configure -a

---

### Post by Raven404 on 2007-10-01
still says 'missing version'. Any force options I should try??

---

### Post by Pumalite on 2007-10-01
Try:
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

