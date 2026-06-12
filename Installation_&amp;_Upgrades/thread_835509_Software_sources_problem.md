---
title: "Software sources problem"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2008-06-20
As I updated from Gutsy to Hardy, Gutsy is shown as the CD rom in the software sources. I tried adding the Hardy CD but it reported it failed to mount. When I physically put the CD in to the drive, it did open a window showing the CD contents.

I have disabled the CD in the softwar sources. Is that OK?


The other error message in the update manager is:

Failed to fetch [http://www.virtualbox.org/debian/dists/hardy/non-free/binary-i386/Packages.gz](http://www.virtualbox.org/debian/dists/hardy/non-free/binary-i386/Packages.gz)  403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.

I manually edited it from gutsy to hardy, but I still get the above error. What should I do?

Robin

---

### Post by Pumalite on 2008-06-20
Disabling CD as a source is OK. Post:
cat /etc/apt/sources.list

---

