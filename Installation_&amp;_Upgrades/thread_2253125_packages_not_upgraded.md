---
title: "packages not upgraded"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by marchello_lippi2 on 2014-11-17
Hi all, 

$ sudo apt-get upgrade -V
Reading packages list... Done
Building dependencies tree
Reading information about state... Done
Upgrades calculating... Done
Packages left unchanged: 
   wine1.7 (1.7.30-0ubuntu1~ppa1 => 1.7.31-0ubuntu1~ppa1)
   wine1.7-i386 (1.7.30-0ubuntu1~ppa1 => 1.7.31-0ubuntu1~ppa1)
upgraded 0, installed 0 new, 0 marked for delete and 2 not upgraded.

What is it and how to solve? 

Lubuntu 14.04.1 LTS

---

### Post by matt_symes on 2014-11-17
Hi

First try

```
sudo apt-get dist-upgrade
```

Post back on that command.

Kind regards

---

### Post by marchello_lippi2 on 2014-11-17
Thanks, works great.

---

