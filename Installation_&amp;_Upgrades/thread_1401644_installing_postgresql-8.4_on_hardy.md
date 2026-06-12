---
title: "installing postgresql-8.4 on hardy"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by axismundi on 2010-02-08
Hi,
we have Ubuntu hardy (8.0.4) and we need to install postgresql 8.4

according to this page it should be possible using hardy-backports:
[http://packages.ubuntu.com/search?keywords=postgresql-8.4](http://packages.ubuntu.com/search?keywords=postgresql-8.4)

I configured sources.list as follows, 
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hardy-backports main
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hardy-updates main restricted universe
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hardy-security main restricted universe


but dpkg -l rejects to list "postgresql-8.4"

Also, apt-get install postgresql=8.4 fails.

Please help how to install postgresql-8.4 package

---

### Post by axismundi on 2010-02-08
solved, i figured out to use -t

---

