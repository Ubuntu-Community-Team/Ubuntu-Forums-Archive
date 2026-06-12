---
title: "[SOLVED] Tried to upgrade via apt-get and got this..."
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by perlluver on 2007-11-03
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  libstreamanalyzer-dev libstreamanalyzer0
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

What is that about?

I tried update manager and I got this error:  See Screenshot.

---

### Post by perlluver on 2007-11-03
```
sudo aptitude update && sudo aptitude upgrade
```

Never mind used the above code and it is working fine.

---

