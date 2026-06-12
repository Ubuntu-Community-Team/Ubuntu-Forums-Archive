---
title: "Downgrading back to default"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by Scifer on 2010-08-21
I upgraded my Lucid Lynx with some PPAs and found some bugs. Now I removed the PPAs and want to downgrade my system according to default repositories. What is the best way to do that?

---

### Post by Scifer on 2010-08-22
Nevermind. ppa-purge will do the trick. ;)

---

### Post by Scifer on 2010-08-22
Unfortunately I cant downgrade Kubuntu.
```
$ sudo ppa-purge ppa:kubuntu-ppa/ppa
PPA to be removed: kubuntu-ppa ppa
Warning:  Could not find package list for PPA: kubuntu-ppa ppa
```Can anyone help me?

---

### Post by Scifer on 2010-08-22
> **Scifer said:**
> Unfortunately I cant downgrade Kubuntu.
```
$ sudo ppa-purge ppa:kubuntu-ppa/ppa
PPA to be removed: kubuntu-ppa ppa
Warning:  Could not find package list for PPA: kubuntu-ppa ppa
```Can anyone help me?
Nevermind. It happened cause my kubuntu-ppa was neither active nor updated.

---

