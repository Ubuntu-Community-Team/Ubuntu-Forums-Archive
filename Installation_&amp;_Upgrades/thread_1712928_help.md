---
title: "help"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by MrStranger on 2011-03-23
i can't install 
ln: creating symbolic link `/usr/bin/nautilus': File exists
dpkg: error processing autoscan (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 autoscan
E: Sub-process /usr/bin/dpkg returned an error code (1)
thx for help

---

### Post by zvacet on 2011-03-25
```
sudo dpkg --configure -a
```

P.S. Next time,please,be more descriptive with thread title.That way you will get help sooner,and help other with similar problem to find solution.

---

### Post by MrStranger on 2011-03-26
thx man for heling it works

---

