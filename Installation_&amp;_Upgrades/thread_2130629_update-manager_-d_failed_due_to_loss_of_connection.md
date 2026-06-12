---
title: "update-manager -d failed due to loss of connection, will now no longer finds 13.04"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by TechVamp on 2013-03-30
I was attempting to upgrade to 13.04 by way of update-manager -d, but halfway through the process, my internet connection failed causing the upgrade process to stop. Now when I run it again, it no longer finds that there is a new distribution to upgrade to. Any advice on fixing this issue?

---

### Post by plucky on 2013-03-30
> Any advice on fixing this issue? 

Without knowing how far it got through the process,it would be difficult for us to say what to do.

Open a terminal and post output for ```
lsb_release -a
uname -a
cat /etc/apt/sources.list
sudo dpkg --configure -a
```

Good Luck

---

