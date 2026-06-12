---
title: "Can't install Scribus"
date: 2016-12-18
forum: Installation &amp; Upgrades
---

### Post by c.shetkar on 2016-12-18
I tried installing Scribus; a publishing software, using the terminal and got the following output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apt-utils : Depends: apt (= 1.3.1) but 1.3.2ubuntu0.1 is to be installed
 scribus : Depends: python-tk but it is not going to be installed
           Depends: scribus-data (= 1.4.6+dfsg-3build1) but it is not going to be installed
           Depends: libpodofo0.9.4 but it is not going to be installed
           Recommends: fonts-dejavu but it is not going to be installed
           Recommends: icc-profiles-free but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
Please help me solve these dependencies.

---

### Post by ajgreeny on 2016-12-18
Which version of *ubuntu are you running and with which DE; I assume it is 16.04?
Did you run command ```
sudo apt-get update
``` before trying to install scribus?

---

