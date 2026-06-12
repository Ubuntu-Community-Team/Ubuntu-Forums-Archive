---
title: "Attempt to install any qt/kde application fails"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Dthdealer on 2009-11-22
Whenever I try to install a kde application I get thrown error messages such as this.
```
The following packages have unmet dependencies:
  kgoldrunner: Depends: kdebase-runtime (>= 4:4.3.2) but it is not going to be installed
               Depends: kdelibs5 (>= 4:4.3.2) but it is not going to be installed
               Depends: libkdegames5 (>= 4:4.3.2) but it is not going to be installed
               Depends: libqt4-dbus (>= 4.5.1) but it is not going to be installed
               Depends: libqt4-phonon (>= 4.5.1) but it is not going to be installed
               Depends: libqt4-xml (>= 4.5.1) but it is not going to be installed
E: Broken packages
```

The message changes depending on the dependencies, but they are always related to kde.

So I tried a **apt-get remove ^kde*** and **apt-get remove ^qt***, but the same errors still come up.

For some reason one of my KDE packages is out of sync with the rest,  but I don't know how to find out which one it is.

**apt-get check** just returns
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```
Giving the impression there are no errors.

How can I find the black sheep among the herd?

---

