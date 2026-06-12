---
title: "skype doesn't install"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by brianv7 on 2013-03-21
I've tried to install skype from software center and it won't it says "error" Package dependencies cannot be resolved:(

what happenend? tanx!

---

### Post by brianv7 on 2013-03-28
thanks 4 all the help everyone:confused:

---

### Post by slickymaster on 2013-03-28
In order to fix your packages dependencies try the following at a terminal window:
```
sudo dpkg --configure -a       
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

Afterwards try to install Skype again.

---

