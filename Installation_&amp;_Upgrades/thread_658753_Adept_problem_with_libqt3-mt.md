---
title: "Adept problem with libqt3-mt"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by robert_rowe on 2008-01-05
just installed Kubuntu 7.10 on a new computer. I'm using the 64 bit addition as the computer is 64 bit. Install went fine. Adept said there were several updates so I told it to fetch them. It downloded them but bombed out while applying them. I think that the culprit is  libqt3-mt. Below is the output from adept. I think that I need to get this package out of the queue so that I can get java installed.

Any help would be appreciated.

Robert Rowe


Selecting previously deselected package sun-java6-bin.
(Reading database ... 89662 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-03-0ubuntu2_amd64.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-03-0ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Setting up libqt3-mt (3:3.3.8really3.3.7-0ubuntu11.1) ...

Configuration file `/etc/qt3/qt_plugins_3.3rc'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** qt_plugins_3.3rc (Y/I/N/O/D/Z) [default=N] ? dpkg: error processing libqt3-mt (--configure):
 EOF on stdin at conffile prompt
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on libqt3-mt (>= 3:3.3.8really3.3.7); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-manager:
 adept-manager depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 adept-manager depends on libqt3-mt (>= 3:3.3.8really3.3.7); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing adept-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-installer:
 adept-installer depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 adept-installer depends on libqt3-mt (>= 3:3.3.8really3.3.7); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing adept-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-updater:
 adept-updater depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 adept-updater depends on libqt3-mt (>= 3:3.3.8really3.3.7); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing adept-updater (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-notifier:
 adept-notifier depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 adept-notifier depends on libqt3-mt (>= 3:3.3.8really3.3.7); however:
  Package libqt3-mt is not configured yet.
 adept-notifier depends on adept-updater; however:
  Package adept-updater is not configured yet.
dpkg: error processing adept-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-batch:
 adept-batch depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 adept-batch depends on libqt3-mt (>= 3:3.3.8really3.3.7); however:
  Package libqt3-mt is not configured yet.
 adept-batch depends on adept-manager; however:
  Package adept-manager is not configured yet.
dpkg: error processing adept-batch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept:
 adept depends on adept-manager; however:
  Package adept-manager is not configured yet.
 adept depends on adept-installer; however:
  Package adept-installer is not configured yet.
 adept depends on adept-updater; however:
  Package adept-updater is not configured yet.
 adept depends on adept-notifier; however:
  Package adept-notifier is not configured yet.
 adept depends on adept-batch; however:
  Package adept-batch is not configured yet.
dpkg: error processing adept (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-bin (6-03-0ubuntu2) ...

Setting up sun-java6-jre (6-03-0ubuntu2) ...

Errors were encountered while processing:
 libqt3-mt
 kdelibs4c2a
 adept-manager
 adept-installer
 adept-updater
 adept-notifier
 adept-batch
 adept

---

### Post by PmDematagoda on 2008-01-05
Execute:-
```
sudo dpkg --configure -a
```
See if that solves your problem.

---

### Post by robert_rowe on 2008-01-05
That did the trick. It seems that the default was to keep my old version and adept was accepting the default. I told it Y and it installed the new version. Now other packages that depend on it install fine.

Thanks a million.

Robert Rowe

---

### Post by squelsh on 2008-02-06
I just switched from Gentoo to Ubuntu and ran into this problem.
Thanx a lot for this tip! The packet management is completely different than in Gentoo...

---

