---
title: "synaptic will not config any files upgrade or new"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by archangel74 on 2008-07-04
this message comes up for every file, no matter what kind. 

Not all changes and updates succeeded.  dpkg: parse error, in file '/var/lib/dpkg/status' near line 26700 package 'findutils':
field name '"been' must be followed by colon
E: subprocess /usr/bin/dpkg reuturned error package (2)

Can anyone expound on this for me?

---

### Post by Pumalite on 2008-07-04
Go to /var/lib/dpkg/status:
gksudo gedit /var/lib/dpkg/status
Find the offending package and fix it.

---

### Post by archangel74 on 2008-07-04
thanks you're the best.  =)

ARchangel

---

### Post by Pumalite on 2008-07-04
You are welcome. Good luck!

---

