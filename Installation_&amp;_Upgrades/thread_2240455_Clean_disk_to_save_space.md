---
title: "Clean disk to save space"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by anthemousios on 2014-08-20
As time passes the free disk space seems to be reduced. How can I clean my disk to save some space

---

### Post by sudodus on 2014-08-20
0. ***Back up*** you system before you start removing things, because you might remove too much ...

1. You can ***remove old kernels*** and leave only the current one and the previous one (so the two newest and working kernels). This is easy to do with Ubuntu Tweak

```
sudo add-apt-repository ppa:tualatrix/ppa


```
Then update the source and install Ubuntu Tweak:

 ```
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

When you have installed, just type to get all packages up to date:

 ```
sudo apt-get dist-upgrade
```

***2.*** You can identify and ***remove files*** that are just filling the disk, multimedia files, iso files, old documents etc. this may be the ***main task***.

3. You can identify and ***remove program packages*** that are just filling the disk.

```
sudo apt-get remove package
```  (use the relevant package name for each package you want to remove).

---

### Post by pfeiffep on 2014-08-20
[COLOR=#DD4814][COLOR=#C61919][sudodus]("http://ubuntuforums.org/member.php?u=1499021") [/COLOR][/COLOR]  provided excellent solution if you want a more streamlined approach I've found that bleachbit keeps my systems clean.

---

