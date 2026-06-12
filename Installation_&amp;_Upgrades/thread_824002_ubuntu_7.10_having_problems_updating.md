---
title: "ubuntu 7.10 having problems updating"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by constantgamer247 on 2008-06-09
i installed 7.10 and plugged the ethernet in, then update manager came up, so I clicked install updates, it downloaded them all, then started to install, but stopped 1/3 of the way through

it gave me this error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

and now I cant install the other 191 updates

plz help
thx in advance gabe

---

### Post by Pumalite on 2008-06-09
sudo dpkg --configure -a

---

### Post by constantgamer247 on 2008-06-09
thx

---

### Post by Pumalite on 2008-06-09
You are welcome. Good luck.

---

