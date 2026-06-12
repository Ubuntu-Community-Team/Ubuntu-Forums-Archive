---
title: "[SOLVED] Can't Uninstall nvidia-343 from xorg-edgers PPA (Broken Package)"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by jonathantmayer1 on 2015-04-16
```
Errors were encountered while processing:
 nvidia-343
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have tried apt-get purge, apt-get autoclean, and apt-get clean, and still get the same problems.

Edit: I loaded safe mode through GRUB, ran the package repair, reinstalled all the packages the previous install removed. All good now.

---

### Post by kc1di on 2015-04-16
try this one```
sudo dpkg --configure -a
```
then try ```
sudo apt-get purge again
```

---

### Post by Keith_Helms on 2015-04-17
Try the following commands
```
sudo apt-get install ppa-purge
sudo ppa-purge xorg-edgers/ppa

```

---

### Post by kc1di on 2015-04-17
What did you do to solve it?  Let us know so others reading this thread will find help.

---

