---
title: "HOWTO: Upgrade to Subversion 1.7"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by Emblem Parade on 2011-11-05
This has been tested on Oneiric, and should work all the way down to Lucid. Simply run these commands in a terminal:

```
echo "deb http://opensource.wandisco.com/ubuntu lucid svn17" | sudo tee /etc/apt/sources.list.d/svn.list
sudo wget -q http://opensource.wandisco.com/wandisco-debian.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get dist-upgrade

```

Note: this is the official repository from WANdisco, and should be considered safe.

Also of note: this repository includes a compatible "libsvn-java" package, which you can then use to run Subclipse 1.8 in JavaHL mode.

You will also have to add this line to your eclipse.ini:

```
-Djava.library.path=/usr/lib/jni
```

---

### Post by adamantivm on 2012-02-27
Worked like a charm. Thank you!

Now I can use Eclipse 3.7 with Subclipse 1.8

---

### Post by fxer on 2012-02-27
Has anyone given this a try on Lucid and run 1.7.x without problems? SVN updates stopped happening with version 1.6.6 on 10.04

EDIT: Just did this on Lucid, everything is working great thanks for the info Emblem Parade

---

### Post by carbontax on 2012-06-11
Works in Pangolin. Thanks very much for the recipe.

---

### Post by KemalBALABAN on 2012-07-28
Hi,
great post.

**Problem: **
org.apache.subversion.javahl.ClientException: SQLite Error
sqlite: no such table: wcroot

---

### Post by taberski on 2012-09-01
Hello,

I just wanted to add that I also was successful with an upgrade to Precise Pangolin (aka 12.04LTS) using these instructions.

Thank you!

Kevin Taberski

---

