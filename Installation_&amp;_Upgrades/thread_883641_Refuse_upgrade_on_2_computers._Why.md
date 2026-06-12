---
title: "Refuse upgrade on 2 computers. Why?"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by svala on 2008-08-08
How do a new user fix this problem which appear on my two computers when I try to upgrade:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

<snip>

Thank You!

Stein Svala

---

### Post by PmDematagoda on 2008-08-08
Are you running another package management process such as Synaptic or apt? If so, close them and try again. If not, then remove the stale lock file with:-
```
sudo rm /var/cache/apt/archives/lock
```

Also, please do not include your e-mail address in public posts as they could be exploited by spammers, therefore it(the address) is removed.

---

