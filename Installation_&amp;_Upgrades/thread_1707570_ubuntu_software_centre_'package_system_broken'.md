---
title: "ubuntu software centre 'package system broken'"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by DanixVx on 2011-03-15
hello, i am trying to install playonlinux using ubuntu software centre, but every time i try it comes up with
 
'the package system is broken' 
if you are using third party respositories then disable them, since they are a common source of problems.
now run the following command in a terminal: apt-get install -f
 
what do i do?
please use beginner talk

---

### Post by zvacet on 2011-03-15
In applications>accessories>terminal type

```
sudo apt-get -f install
```

---

