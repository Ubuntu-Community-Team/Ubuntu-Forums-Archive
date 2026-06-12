---
title: "Upgrade Problem with desktopcouch (Lucid -&gt; Natty)"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by cyclohexan on 2011-05-07
Hello,
I've tried a dist-upgrade from Lucid to Natty. Some packages have been installed, but now desktopcouch is causing problems:

```
**sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 desktopcouch : Depends: python-desktopcouch-application (= 1.0.7-0ubuntu2) but it is not installed
E: Unmet dependencies. Try using -f.
```

The solution suggested by apt-get doesn't work either:

```
**sudo apt-get -f install**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libqt4-assistant libsoundtouch1c2 ttf-dejavu-extra install-package usb-creator-gtk usb-creator-common libmowgli1 openoffice.org-style-crystal gdebi-kde
  ttf-dejavu kdepimlibs5 libkholidays4 libmodplug0c2 xaw3dg packagekit-backend-apt libsdl-image1.2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-desktopcouch-application python-desktopcouch-records
The following NEW packages will be installed:
  python-desktopcouch-application
The following packages will be upgraded:
  python-desktopcouch-records
1 upgraded, 1 newly installed, 0 to remove and 451 not upgraded.
593 not fully installed or removed.
Need to get 0 B/59.2 kB of archives.
After this operation, 303 kB of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 506189 files and directories currently installed.)
Preparing to replace python-desktopcouch-records 0.6.4-0ubuntu3.2 (using .../python-desktopcouch-records_1.0.7-0ubuntu2_all.deb) ...
Unpacking replacement python-desktopcouch-records ...
dpkg: error processing /var/cache/apt/archives/python-desktopcouch-records_1.0.7-0ubuntu2_all.deb (--unpack):
 trying to overwrite '/usr/share/pyshared/desktopcouch/__init__.py', which is also in package python-desktopcouch 0.6.4-0ubuntu3.2
Unpacking python-desktopcouch-application (from .../python-desktopcouch-application_1.0.7-0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python-desktopcouch-application_1.0.7-0ubuntu2_all.deb (--unpack):
 trying to overwrite '/usr/share/pyshared/desktopcouch/pair/couchdb_pairing/__init__.py', which is also in package python-desktopcouch 0.6.4-0ubuntu3.2
No apport report written because MaxReports is reached already
                                                              Processing triggers for python-central ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-desktopcouch-records_1.0.7-0ubuntu2_all.deb
 /var/cache/apt/archives/python-desktopcouch-application_1.0.7-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas?

---

### Post by cyclohexan on 2011-05-07
This helped:



sudo dpkg --configure -a

sudo apt-get remove python-desktopcouch-records desktopcouch evolution-couchdb python-desktopcouch

---

