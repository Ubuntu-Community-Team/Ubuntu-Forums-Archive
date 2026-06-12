---
title: "Apt-Crazy"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by beradero on 2011-08-11
Hello,
I'm trying to install liblua50-dev, but I keep getting this error:

```
The following extra packages will be installed:
  liblua50 liblualib50 lua50
The following NEW packages will be installed:
  liblua50 liblua50-dev liblualib50 lua50
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 169kB of archives.
After this operation, 692kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Err http://br.archive.ubuntu.com/ubuntu/ maverick/universe liblua50 i386 5.0.3-4
  404  Not Found
Err http://br.archive.ubuntu.com/ubuntu/ maverick/universe liblualib50 i386 5.0.3-4
  404  Not Found
Err http://br.archive.ubuntu.com/ubuntu/ maverick/universe lua50 i386 5.0.3-4
  404  Not Found
Err http://br.archive.ubuntu.com/ubuntu/ maverick/universe liblua50-dev i386 5.0.3-4
  404  Not Found
```

Apt is trying to fetch the 5.0.3-**4** version, but the [repo]("http://br.archive.ubuntu.com/ubuntu/pool/universe/l/lua50/") only list the 5.0.3-**6** version..
I tried apt-get update several times, but it don't fix the problem.. 

What now?

---

### Post by dino99 on 2011-08-11
download from the main server instead of the localized br (synaptic setting)

and check that you are using maverick (not mixed repo)

---

### Post by beradero on 2011-08-11
I'm using the man mirror now, and it worked fine.
How can I report that bug to the br mirror?

Thanks!

---

### Post by dino99 on 2011-08-11
its some kind of common with many localized mirrors, but dont worry too much and simply switch server if there is a conflict with a non fully updated base.

---

