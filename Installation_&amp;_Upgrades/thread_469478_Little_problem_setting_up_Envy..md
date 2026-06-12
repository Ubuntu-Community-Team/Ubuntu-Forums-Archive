---
title: "Little problem setting up Envy."
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by mu:te on 2007-06-09
Good morning ya all,

For the last month I've been trying to set up ATi driver without any good results, only got in the shi***est problems ever.

To make a long story a short story this is what I get when I write "dpkg - i path-to-envy-deb.

(```
Reading database ... 134659 files and directories currently installed.)
Preparing to replace envy 0.9.4-0ubuntu6 (using envy_0.9.4-0ubuntu6_all.deb) ...
Unpacking replacement envy ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy
```

Help asap would be greatly wanted! ;)

---

### Post by empthollow on 2007-06-09
try installing the packages it says it requires.
```
sudo apt-get -y install xserver-xorg-dev dpatch
```

---

