---
title: "problem while installation"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by vickysodhi67 on 2013-09-12
While installing something it gives an error of E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?:evil::evil:
Please help me...

---

### Post by Quackers on 2013-09-12
Could you have been using 2 events of installing or uninstalling something at the same time? That would so it I think.

---

### Post by vickysodhi67 on 2013-09-12
yipp now its working thanxx...

---

### Post by Quackers on 2013-09-12
Excellent  :D
Yes, only one instance of dpkg can run at any one time.
Have fun!

---

