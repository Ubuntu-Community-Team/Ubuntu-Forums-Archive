---
title: "dictionaries-common failed to upgrade from oneiric to precise: no more xemacs!"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by jobarjo on 2012-05-10
Hi

I recently upgraded from oneiric to precise 32bit.

It seems that I suffer from this bug too:
[https://bugs.launchpad.net/ubuntu/+source/dictionaries-common/+bug/927464](https://bugs.launchpad.net/ubuntu/+source/dictionaries-common/+bug/927464)

xemacs21 was not working correctly. So I uninstalled it.

The consequence is that I can't use xemacs21 anymore, and it is my main programming tool!

I can't install it anymore.
I have the exact same symptom as in this (closed) thread:
[http://ubuntuforums.org/showthread.php?t=1900351](http://ubuntuforums.org/showthread.php?t=1900351)

I even tried dpkg-reconfigure -a, bit it is the same:
```
# apt-get install --reinstall xemacs21
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  emacsen-common xemacs21-bin xemacs21-mule xemacs21-support
Suggested packages:
  xemacs21-supportel
The following NEW packages will be installed:
  emacsen-common xemacs21 xemacs21-bin xemacs21-mule xemacs21-support
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/7,164 kB of archives.
After this operation, 17.2 MB of additional disk space will be used.
Do you want to continue [Y/n]?
Selecting previously unselected package emacsen-common.
(Reading database ... 185060 files and directories currently installed.)
Unpacking emacsen-common (from .../emacsen-common_1.4.22ubuntu1_all.deb) ...
Selecting previously unselected package xemacs21-support.
Unpacking xemacs21-support (from .../xemacs21-support_21.4.22-3.2ubuntu1_all.deb) ...
Selecting previously unselected package xemacs21-bin.
Unpacking xemacs21-bin (from .../xemacs21-bin_21.4.22-3.2ubuntu1_i386.deb) ...
Selecting previously unselected package xemacs21-mule.
Unpacking xemacs21-mule (from .../xemacs21-mule_21.4.22-3.2ubuntu1_i386.deb) ...
Selecting previously unselected package xemacs21.
Unpacking xemacs21 (from .../xemacs21_21.4.22-3.2ubuntu1_all.deb) ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/xemacs21/emodules.info.gz'
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up emacsen-common (1.4.22ubuntu1) ...
emacsen-common: Handling install of emacsen flavor emacs
emacsen-common: Handling install of emacsen flavor xemacs21
emacsen-common: byte-compiling for xemacs21
/usr/lib/emacsen-common/packages/install/emacsen-common: 38: /usr/lib/emacsen-common/packages/install/emacsen-common: xemacs21: not found
emacs-package-install: /usr/lib/emacsen-common/packages/install/emacsen-common xemacs21 xemacs21 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing emacsen-common (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-mule:
 xemacs21-mule depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-mule (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xemacs21:
 xemacs21 depends on xemacs21-mule (>= 21.4.22-3.2ubuntu1) | xemacs21-mule-canna-wnn (>= 21.4.22-3.2ubuntu1) | xemacs21-nomule (>= 21.4.22-3.2ubuntu1); however:
No apport report written because MaxReports is reached already  
                                                                Package xemacs21-mule is not configured yet.
  Package xemacs21-mule-canna-wnn is not installed.
  Package xemacs21-nomule is not installed.
dpkg: error processing xemacs21 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xemacs21-support:
 xemacs21-support depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
 xemacs21-support depends on xemacs21 (= 21.4.22-3.2ubuntu1); however:
  Package xemacs21 is not configured yet.
dpkg: error processing xemacs21-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xemacs21-bin:
 xemacs21-bin depends on xemacs21-support (= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-support is not configured yet.
dpkg: error processing xemacs21-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                   Errors were encountered while processing:
 emacsen-common
 xemacs21-mule
 xemacs21
 xemacs21-support
 xemacs21-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help. I will have to compile from source...

---

