---
title: "Installation Problems"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by Bookiescit on 2007-12-28
Every time I try to add a new software I get the same message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can anyone help me wit this problem? I have no Idea wat to do.

I am useing a IBM laptop that had windows xp on it and I want to move away from XP.

HELP!!!!!

---

### Post by taurus on 2007-12-28
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

