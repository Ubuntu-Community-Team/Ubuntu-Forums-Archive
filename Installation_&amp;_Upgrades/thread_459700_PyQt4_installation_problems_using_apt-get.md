---
title: "PyQt4 installation problems using apt-get"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by MagisterJoe on 2007-05-30
I'm trying to install python-qt4 and python-qt4-dev so that I can build a few PyQt4 GUIs from some Qt Designer 4 files.  When I run apt, I get:

```
sudo apt-get install python-qt4
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-qt4: Depends: libqt4-core (>= 4.2.2) but it is not going to be installed
              Depends: libqt4-gui (>= 4.2.2) but it is not going to be installed
E: Broken packages
```

It turns out that I have libqt4-core-kdecopy installed (using Kubuntu), which is blocking the installation of libqt4-core.  Same for all other libqt4 files.  That seems fine, except that the package manager isn't smart enough to tell python-qt4 to use these libqt4 files instead.  What can I do so that I don't screw up my KDE desktop but still get PyQt4?

---

### Post by MagisterJoe on 2007-05-31
Anybody?

---

