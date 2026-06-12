---
title: "Why is SPM trying to install automatix2 for edgy on a dapper"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by fjm03 on 2007-01-25
Since I've installed automatix2 on dapper, the SPM keeps trying to upgrade to the automatix2 version for edgy which 1) won't run on dapper and 2) removes the version that will run on dapper.

How do I turn off the faucet?  I'm tired of seeing the update icon appear and then find an offer for an unusable app.

---

### Post by Ptero-4 on 2007-01-25
It might help to just remove automatix. IIRC it's only function is to enable some repos and install some propietary stuff (both are one-time jobs, so automatix should be required after those jobs have been performed).

---

### Post by taurus on 2007-01-25
Or look in /etc/apt/sources.list and make sure you have only **dapper** in there instead of **edgy**.

```
cat /etc/apt/sources.list
```

---

### Post by jackrobinson on 2007-01-26
> **fjm03 said:**
> Since I've installed automatix2 on dapper, the SPM keeps trying to upgrade to the automatix2 version for edgy which 1) won't run on dapper and 2) removes the version that will run on dapper.

How do I turn off the faucet?  I'm tired of seeing the update icon appear and then find an offer for an unusable app.

because you mistakenly installed Automatix2 for Edgy which added the edgy repository for Automatix2.
remove the following line from your /etc/apt/sources.list
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main 
and do a ```
sudo apt-get update
```
and the annoyance will disappear. If you want to use Automatix2 on Dapper however, make sure you have the correct repo added (with no duplicates)
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by fjm03 on 2007-01-26
Found the offending line and deleted it. 
Did an update and the repo list came up all dapper. Icon gone.
I appreciate the utility of AX2. Went through the terminal install process to learn about Ubuntu (sudo).
Made mistakes but Arnieboy and the Ubuntu community was at the ready to bail me out.
Thanks to all of you (Petro-4, tarus and jackrobinson).

---

