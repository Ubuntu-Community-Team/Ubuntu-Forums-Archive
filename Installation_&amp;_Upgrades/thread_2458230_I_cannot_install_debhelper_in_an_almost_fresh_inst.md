---
title: "I cannot install debhelper in an almost fresh install"
date: 2021-02-19
forum: Installation &amp; Upgrades
---

### Post by firthu on 2021-02-19
I am unable to install debhelper in 20.04 (installed 01-feb-2021):

"Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'debhelper' has no installation candidate
"

I have an almost fresh install
I don't have errors while doing the general apt commands clean etc.

cat /var/log/apt/history.log 
[https://pastebin.com/BAw7YEUs](https://pastebin.com/BAw7YEUs)

grep ^deb -r /etc/apt/ --include=*.list
[https://pastebin.com/TqZ1xwxk](https://pastebin.com/TqZ1xwxk)

---

### Post by schragge on 2021-02-19
I don't see
```
deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
```
in your **/etc/apt/sources.list**.

---

### Post by grahammechanical on 2021-02-19
According to this web site the repository is focal main

[https://ubuntu.pkgs.org/20.04/ubuntu-main-amd64/debhelper_12.10ubuntu1_all.deb.html](https://ubuntu.pkgs.org/20.04/ubuntu-main-amd64/debhelper_12.10ubuntu1_all.deb.html)

Regards

---

### Post by schragge on 2021-02-19
While at it, add this line as well:
```
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
```

---

