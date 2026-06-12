---
title: "Ubuntu 12.04 in place upgrade still possible?"
date: 2020-11-05
forum: Installation &amp; Upgrades
---

### Post by eclay on 2020-11-05
Hello,  we have some old ubuntu 12.04 servers in the wild and I'm wondering if it's still possible to do the rolling upgrade to 14.04 -> 16.04 -> 18.04?

---

### Post by Impavidus on 2020-11-05
Theoretically, yes, but you're 2 upgrades away from the first supported release and 4 upgrades from the latest LTS release, so that would be a 4 to 8GB download and 5 to 10 hours installing and, as many things changed, you'd still spend hours reconfiguring, if it still works well enough that you can get to the reconfiguring stage. Probably better to start with a fresh install.

---

### Post by wildmanne39 on 2020-11-05
Back up important data and do a fresh install it will save you a lot of headaches, there have been so many changes in Ubuntu since 12.04 you will most likely make your system unusable and it will take hours and hours to update where a fresh install only a few minutes.

---

### Post by grahammechanical on 2020-11-05
If you like living on the edge this is the wiki page to follow

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

### Post by ActionParsnip on 2020-11-05
You can boot to the ISO of each EOL release and upgrade. It'll be slow and applications may not just work (FreeRadius 2 is very different to FreeRadius 3).
I suggest you install some new servers parallel to the old ones. Set up the functionality and test then decom the old boxes

---

