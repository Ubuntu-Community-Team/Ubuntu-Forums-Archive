---
title: "Where is swat?"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by binett on 2005-09-10
Hi - newbie to ubuntu ... I've installed samba, got the service running, but cannot seem to run swat via locahost:901 ("connection timed out"). I cant even seem to locate the swat executable (it's not in the usual places) and apt-get only gives me the ability to re-install the entire samba (which i've done). Any ideas as to:

1. How to verify if I even have swat?
2. if not, how to explicitly obtain it?

Thanks!

---

### Post by SFN on 2005-09-11
Do
```
sudo apt-get install swat
``` 
If it's already installed, it will tell you so. If it's not, it will install it.

---

### Post by binett on 2005-09-11
Fixed!  for some reason, synaptic didn't show it as a seperate pkg, but apt-cache search and apt-get worked.  Thanks!

---

