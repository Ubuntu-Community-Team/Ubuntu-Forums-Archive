---
title: "system &amp; kernelUpdates and repository error"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by rpk94 on 2011-12-29
I am trying to update my system, it says that my system is up to date, but when I check for updates manually, it says 
> W:Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead. It also tells me to check my internet connection. So my kernel is not upgraded (I still have 3.0.0.14 while my friend who did a fresh install has 3.2.0.7) nor do I get system updates. How do I fix the repo problem without having to reinstall?

---

### Post by 2F4U on 2011-12-30
The third party ppa does not provide packages for 11.10 (oneiric). You can check that by going to the URL

[http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/)

You can remove the third party repository and then everything should work as normal.

---

### Post by rpk94 on 2011-12-30
But then, why am i not getting a kernel upgrade?

---

### Post by critin on 2011-12-30
Are you both using the exact same version of os?  You can download the kernel from launchpad.net

---

