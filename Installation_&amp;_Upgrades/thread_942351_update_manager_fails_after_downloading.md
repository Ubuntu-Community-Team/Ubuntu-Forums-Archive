---
title: "update manager fails after downloading"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by thegreats15 on 2008-10-09
hi,

when updating i got this mess::

> 
Extracting templates from packages: 100%
dpkg: too-long line or missing newline in `/var/lib/dpkg/diversions'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.    Trying to recover:


i am new with this ubuntu....

thegreats15

---

### Post by Sef on 2008-10-09
From the Terminal, (Applications > Accessories > Terminal), paste or type these two commands:

```
sudo apt-get -f install
```then

```
sudo dpkg --configure -a
```

---

