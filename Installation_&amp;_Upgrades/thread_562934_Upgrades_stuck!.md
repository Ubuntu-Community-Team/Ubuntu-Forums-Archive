---
title: "Upgrades stuck!"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by dagvei on 2007-09-29
Downloaded a pre-release og 7.10 yesterday (tribe 5?), and I was very much impressed with everything until the automatic update process started. Fetching upgrades were ok, but everytime I try, it stoppes during the installation of so colled PAM-files. I get a message telling me to restart. When I do, all graphic symbols in the many are gone, rest is ok. BUT; when I try to continue upgrading, I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

As a newbie, I tried to run this command in a terminal, with no luck. What to do?

---

### Post by Pumalite on 2007-09-29
Post complete output of:
sudo apt-get update.

---

### Post by bapoumba on 2007-09-29
Have you tried:
```
sudo dpkg --configure -a
```

---

### Post by dagvei on 2007-09-29
You got it, bapoumba! It has continued the upgrading now! Thanks a lot!!
The 7.10 seems great, by the way!!!

---

### Post by bapoumba on 2007-09-29
Nice :)
Glad to see you got it to work!

---

