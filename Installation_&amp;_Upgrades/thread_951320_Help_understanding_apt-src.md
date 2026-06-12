---
title: "Help understanding apt-src?"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by sci-fi guy on 2008-10-18
Could someone help me understand better what 'apt-src' is for and why one would want to use it?

---

### Post by Partyboi2 on 2008-10-18
If the src lines are enabled it means that ubuntu will pull the source package from the repos, where as deb will pull the binary package from the repo's.

So if you have  the src repo enabled you could download the source of a package with
```
apt-get source package
``` which would download 3 files [FONT=Times][SIZE=3][FONT=Times]a .orig.tar.gz ,  .diff.gz and a .dsc
[/FONT][/SIZE][/FONT]

---

### Post by sci-fi guy on 2008-10-18
Does it automatically compile and install the package?
Is it interchangeable with apt-get?

---

### Post by Partyboi2 on 2008-10-18
No it does not automatically compile and install the package. you would need to use other tools to do that..

---

