---
title: "error wen opening Synaptic Package Manager"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by uKEN on 2011-09-09
well I was instaling wine it frozz so I rebooted and now wen I try to open Synaptic Package Manager I get this error :eek:

'E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.'

how do I run sudo

---

### Post by whatthefunk on 2011-09-09
Open a terminal and enter the following:
```
sudo dpkg --configure -a
```

You will have to enter your password.

---

### Post by uKEN on 2011-09-13
nice...thank you

---

