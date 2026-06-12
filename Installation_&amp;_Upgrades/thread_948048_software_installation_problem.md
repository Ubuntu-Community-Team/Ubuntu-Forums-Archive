---
title: "software installation problem"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by acerhaha on 2008-10-14
Im brand new to this whole ubuntu linux thing and i am having a problem with installing software from the add/remove package manager...it says dpkg interrupted followe by "you must manually run 'dpkg --configure -a'to correct the program.

then it says:
E: _cache-> open() failed, please report......


diagnoses? what does this mean? how can i correct:confused:

---

### Post by Partyboi2 on 2008-10-14
Open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --configure -a
```

---

