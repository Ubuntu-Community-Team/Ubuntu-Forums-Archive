---
title: "libatml issues"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by darkare on 2008-02-14
can anyone please explain this?

I do sudo apt-get dist-upgrade
and I get this

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libatm1 patch
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

I am running 6.06 Dapper Drake

I would appreciate any help trying to resolve this.

---

### Post by zvacet on 2008-02-14
Do you have all repositories open like [this](https://help.ubuntu.com/community/Repositories/Ubuntu)?

---

### Post by darkare on 2008-02-21
I looked at the repositories and it appears that it is ok. I tried to run the dist-upgrade and get the same thing. I don't understand what it is looking for or what it needs.

---

### Post by zvacet on 2008-02-21
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by darkare on 2008-03-11
I run that and this is what I still get.

The following packages have been kept back:
  libatm1 patch
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


:confused:

---

### Post by zvacet on 2008-03-11
Find that packages in synaptic and mark for upgrade.You can not do dist-upgrade if your system is not up-to-date.

---

