---
title: "can't do apt-get update, sources.list and network is okay"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by indosupremacy on 2008-04-11
hi,it has been 2 weeks for me since i can't do apt-get update .
it say like this 
Failed to fetch [http://kambing.vlsm.org/ubuntu/dists/gutsy-security/universe/source/Sources.bz2](http://kambing.vlsm.org/ubuntu/dists/gutsy-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

i have check my sources.list and everyhting is okay. i have change the repository to main server ,but the same condition still happen.
i have run dpkg --configure -a, apt-get clean ,apt-get check...and others thing but the bad thing still happen.
does anybody know what happen to my lovely ubuntu? for your note this thing is happen after i was installing program and suddenly the electricity is down.after reboot i can't do apt-get update...
please help me...thanks

---

### Post by zvacet on 2008-04-11
**System>admin>software sources<third party>uncheck** that repository and reload.

```
sudo apt-get update && sudo apt-get upgrade
```

---

