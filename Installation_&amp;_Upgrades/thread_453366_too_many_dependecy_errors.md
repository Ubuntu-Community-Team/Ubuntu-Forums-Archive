---
title: "too many dependecy errors"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by poision_heart on 2007-05-24
hi i m using feisty on my compaq laptop everything is working good here but as tried to install other packages which i downloaded from internet  they are showing depency not satisfiable error..please guide me how to install those packages...here below i m writing exact errors which i m getting


1. opera9.21   - error:dependecy is not satisfiable:  libqt3-mt

2. alien8.5       - error:dependecy is not satisfiable:  debhelper

3.ymessenger - error:dependecy is not satisfiable:  libgdk-pixbuf2

4.beagle          - error:dependecy is not satisfiable:  libwv-1.2-3

5.checkgmail    - error:dependecy is not satisfiable:  libgtk2-trayicon-perl

6.kmoney2      - error:dependecy is not satisfiable:  kdelibs4

please help me to overcome this prob..

---

### Post by tgm4883 on 2007-05-24
Don't download programs to install unless they are not in the repos or you need a different version for whatever reason.

> 2. alien8.5 - error:dependecy is not satisfiable: debhelper
4.beagle - error:dependecy is not satisfiable: libwv-1.2-3
5.checkgmail - error:dependecy is not satisfiable: libgtk2-trayicon-perl

For instance, you can get these by
```
sudo apt-get install beagle checkgmail alien
```
That will install these three and resolve any dependencies

> hi i m using feisty on my compaq laptop everything is working good here but as tried to install other packages which i downloaded from internet they are showing depency not satisfiable error..please guide me how to install those packages...here below i m writing exact errors which i m getting

1. opera9.21 - error:dependecy is not satisfiable: libqt3-mt

3.ymessenger - error:dependecy is not satisfiable: libgdk-pixbuf2

6.kmoney2 - error:dependecy is not satisfiable: kdelibs4

please help me to overcome this prob..

These I didn't find in the repos, but I did find the dependencies

so apt-get the dependencies then install the software

---

