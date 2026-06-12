---
title: "make not installed"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by WNxCryptic on 2008-01-19
I'm working on a development server and when I go to use make, I find that its not installed!

```
apt-get install make
```

Works but does not configure make, since even after the installation "make" comes up with some information about gcc: command not found.

How do I install / configure the make command in a CLI?

---

### Post by yabbadabbadont on 2008-01-19
You need to install the build-essential package, probably along with automake, autoconf, and libtool.

---

### Post by Pumalite on 2008-01-19
sudo apt-get install build-essential

---

