---
title: "Problem with keys of repos?"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by gasparov on 2005-04-20
Hi,
   I just fugured out now that it's not enough to change references from warty to hoary to have a complete apt sources.list...so as in the guide i changed my repositories to the new ones and followed the encryption suggestions...when I try apt-get update I have the following

```
Hit ftp://ftp.nerim.net testing/main Packages
Ign http://backports.ubuntuforums.org hoary-backports/restricted Packages
Ign http://backports.ubuntuforums.org hoary-extras/main Packages
Hit http://us.archive.ubuntu.com hoary/main Packages
Ign http://backports.ubuntuforums.org hoary-extras/universe Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Ign http://backports.ubuntuforums.org hoary-extras/multiverse Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Ign http://backports.ubuntuforums.org hoary-extras/restricted Packages
Hit http://us.archive.ubuntu.com hoary/universe Packages
Get:6 http://backports.ubuntuforums.org hoary-backports/main Packages [4568B]
Hit http://us.archive.ubuntu.com hoary/universe Sources
Get:7 http://backports.ubuntuforums.org hoary-backports/universe Packages [3827B]
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Get:8 http://backports.ubuntuforums.org hoary-backports/multiverse Packages [20B]
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages

```


Does that  "Ign" of any backport stand for ignored?what's the problem?

---

### Post by Burgundavia on 2005-04-20
There currently are not Hoary backports. So the repo is failing and being IGNored.

Corey

---

