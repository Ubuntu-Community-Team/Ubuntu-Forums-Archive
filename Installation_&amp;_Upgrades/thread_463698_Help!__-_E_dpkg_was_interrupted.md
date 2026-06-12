---
title: "Help!  - E: dpkg was interrupted"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by Tippmann5150 on 2007-06-03
when trying to install, i get this error:

E: dpkg was interrupted, you must manually run "dpkg --configure -a" to crorrect the problem.


After running dpkg --configure -a

i get:

dpkg: parse error, in file `/var/lib/dpkg/updates/0013' near line 1:
 newline in field name `#padding'



i am so confused :(

---

### Post by zvacet on 2007-06-04
```
sudo dpkg --configure -a
```

---

### Post by Tippmann5150 on 2007-06-04
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

Like i said in my first post:


> After running dpkg --configure -a

i get:

dpkg: parse error, in file `/var/lib/dpkg/updates/0013' near line 1:
newline in field name `#padding'


---

### Post by zvacet on 2007-06-04
it is seems to be missunderstanding between us.I understand from your post that you runed command without sudo,and that is why replay to you.

---

### Post by Tippmann5150 on 2007-06-04
ah, sorry. i did use sudo

---

