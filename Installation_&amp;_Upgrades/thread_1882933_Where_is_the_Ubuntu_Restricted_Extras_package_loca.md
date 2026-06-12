---
title: "Where is the Ubuntu Restricted Extras package located?"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by jasoncruz98 on 2011-11-18
I have a slow connection. After I install ubuntu-restricted-extras package into my system, I plan to back it up on another USB drive. The problem is, where are these files located?

---

### Post by mick222 on 2011-11-18
Look in var/cache/apt/archives you should find the .deb file there.
You can use apt ton cd to create a snapshot of your system and use that to install on another computer I think never tried it.

---

### Post by tartalo on 2011-11-18
Take in account that it's a metapackage, the important packages are the ones that it depends on.

[http://askubuntu.com/questions/45208/how-can-i-install-restricted-extras-offline](http://askubuntu.com/questions/45208/how-can-i-install-restricted-extras-offline)

---

