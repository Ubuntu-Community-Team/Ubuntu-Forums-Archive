---
title: "Error when updating."
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by zoorocket on 2008-11-05
I get these errors when trying to update.

> E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Any idea on how to fix this?

---

### Post by taurus on 2008-11-05
Do you have apt-get or apt running in the background?  You can look for it from the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
ps -A
```

---

