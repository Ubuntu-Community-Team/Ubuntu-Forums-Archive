---
title: "Installing Qtstalker 0.32"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by xice on 2006-07-04
I notice 0.26 is in the universe/multiverse repository, how could i install qtstalker 0.32, i seem to not be able to,

[http://sourceforge.net/projects/qtstalker/](http://sourceforge.net/projects/qtstalker/)

---

### Post by Jagot on 2006-07-04
On the page you provided, when you go to download you can download the .deb version of the file.

The you need to go to Terminal and navigate to wherever you've downloaded, then:

```
sudo dpkg -i qtstalker_0.32-1_i386.deb
```

---

### Post by xice on 2006-07-05
Whilst sure, the above command would usually work no problems, i have a big package discrepancy. namely between  libqt3c102-mt and libqt3-mt.
So if i force install this package the above lib's dont want to be side to side, so i get a package discrepancy. I need libqt3-mt for amarok, of which i dont want to lose. What should i do to have qtstalker 0.32 and amarok installed with no broken packages?

```

ben@xice:~/installers$ sudo dpkg -i qtstalker_0.32-1_i386.deb
Selecting previously deselected package qtstalker.
(Reading database ... 152536 files and directories currently installed.)
Unpacking qtstalker (from qtstalker_0.32-1_i386.deb) ...
dpkg: dependency problems prevent configuration of qtstalker:
 qtstalker depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing qtstalker (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
qtstalker


ben@xice:~/installers$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
ben@xice:~/installers$



ben@xice:~/installers$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
ben@xice:~/installers$


```

---

### Post by Fra Ubu on 2006-12-01
UP...i'm in the same stop-point! using dapper i can install a very old&bugged version, but for edgy is ready the latest...why?

---

