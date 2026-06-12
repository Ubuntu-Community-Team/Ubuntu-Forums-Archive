---
title: "Things to do after installing Ubuntu 12.04"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by dgharmon on 2012-08-26
I get [this error]("http://pastebin.com/LpDQXSxc") when I run [this script]("http://howtoubuntu.org/things-to-do-after-installing-ubuntu-12-04-precise-pangolin/"), any solutions?

---

### Post by zvacet on 2012-08-27
Try with 

```
sudo dpkg --configure -a
```

---

### Post by dgharmon on 2012-08-27
> **zvacet said:**
> Try with 

```
sudo dpkg --configure -a
```

Done that .. then I also did the following as per some other suggestion ...

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

... seems to be working, no damage done :)

---

