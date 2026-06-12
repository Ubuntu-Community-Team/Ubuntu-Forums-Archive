---
title: "apt-get update error"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by ittiam on 2007-05-19
Hi when am trying to do an apt-get update ... i get the following error

> Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages [193kB]
99% [7 Packages gzip 0]                               
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)

Can anyone tell what the problem could be. I did do sudo aptitude update...i get the same error.

---

### Post by taurus on 2007-05-19
Open a terminal and edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from your repos.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ittiam on 2007-05-19
Thanks. That fixed it!

---

