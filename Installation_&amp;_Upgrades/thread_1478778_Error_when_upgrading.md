---
title: "Error when upgrading"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by redshoes702 on 2010-05-10
I tried to upgrade to 10.04, but did not succeed. Error: You have held broken packages. Can anyone tell me how to solve this problem?

---

### Post by mörgæs on 2010-05-10
It is very likely that a clean install would solve the problem. 

Otherwise you could try the following on a newly booted machine:

```
sudo apt-get clean

sudo apt-get update

sudo apt-get upgrade

```

---

### Post by kansasnoob on 2010-05-10
It would be helpful to see any terminal output of:

```
sudo apt-get -f install
```

and also:

```
sudo dpkg --configure -a
```

---

