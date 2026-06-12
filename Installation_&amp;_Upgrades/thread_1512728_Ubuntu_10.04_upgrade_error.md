---
title: "Ubuntu 10.04 upgrade error"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by soadrocks79 on 2010-06-18
While upgrading to ubuntu my update manager just closed and said that ubuntu 10.04 had installed with some errors. I ignored it but now when i try to start ubuntu up it just doesnt start. It will go to a purple loading screen but it will never load and i have no clue what to do. One time it asked me to fix the problem but then it never actually fixed it and the recovery isnt helping. I have no clue how to fix it or what to do, please help.

---

### Post by zvacet on 2010-06-25
Boot in recovery mode and type

```
dpkg --configure -a
```

or if that doesn´t help 

```
apt-get -f install
```

```
apt-get update && apt-get upgrade
apt-get dist-upgrade
```

---

