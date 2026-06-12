---
title: "apt-get dselect-upgrade error"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by kizzmyanthia on 2010-11-14
I am currently executing the following:

(I am running the terminal under root)

```
apt-get dselect-upgrade
```It runs for a few seconds and then returns:
```

dpkg: unrecoverable fatal error, aborting:
  fork failed: Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```and then if I run:

```
dpkg --configure -a
```and then:

```
apt-get -f install
```The package will install.

The problem is that I have 614 packages left to install and if I have to do them one by one, I will be doing installation for approximately 8 months


ANYONE HAVE ANY KIND OF SUGGESTION OR SOLUTION PLEASE HELP!!!

---

### Post by kizzmyanthia on 2010-11-14
bump bump

---

