---
title: "Error in Synaptic Package Manager"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by davidq25 on 2011-09-08
Hi I was trying to install Lubuntu restricted-extra in Synaptic Package Manager and during the installation, I had to turn off my computer. Now when I try to run Synaptic Package Manager, I get:
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

How can I fix this problem?

Thanks for the help

---

### Post by saltmarshlamb on 2011-09-08
You need to open a terminal and run the command it gave you.

```
sudo dpkg --configure -a
```

---

