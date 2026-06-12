---
title: "dpkg problem E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-12-24
forum: Installation &amp; Upgrades
---

### Post by jwshocknesse on 2014-12-24
The problem started after I tried to install python on my machine, I think I accidentally changed a path incorrectly can someone help. Or gave python default execution I'm not sure but, it changed some of my files to .py

Setting up libglib2.0-dev (2.40.2-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package libglib2.0-dev (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lsb-release (4.1+Debian11ubuntu6mint1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package lsb-release (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing package python-apt (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cairo (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-chardet (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of python-commandnotfound:
 python-commandnotfound depends on lsb-release; however:
  Package lsb-release is not configured yet.
 python-commandnotfound depends on python-apt; however:
  Package python-apt is not configured yet.


dpkg: error processing package python-commandnotfound (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing package python-configglue (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-crypto (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-cupshelpers (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-dbus (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of python-debian:
 python-debian depends on python-chardet; however:
  Package python-chardet is not configured yet.


dpkg: error processing package python-debian (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing package python-gi (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-gobject-2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-cairo (>= 1.0.2-1.1); however:
  Package python-cairo is not configured yet.
 python-gtk2 depends on python-gobject-2 (>= 2.21.3); however:
  Package python-gobject-2 is not configured yet.


dpkg: error processing package python-gtk2 (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing package python-httplib2 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Setting up python-keyring (3.5-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-keyring (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-lazr.uri (1.0.3-1build1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-lazr.uri (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-simplejson (3.3.1-1ubuntu6) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-simplejson (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-wadllib:
 python-wadllib depends on python-lazr.uri; however:
  Package python-lazr.uri is not configured yet.


dpkg: error processing package python-wadllib (--configure):
 dependency problems - leaving unconfigured
Setting up python-oauth (1.0.1-3build2) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-oauth (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-lazr.restfulclient:
 python-lazr.restfulclient depends on python-httplib2; however:
  Package python-httplib2 is not configured yet.
 python-lazr.restfulclient depends on python-lazr.uri; however:
  Package python-lazr.uri is not configured yet.
 python-lazr.restfulclient depends on python-simplejson; however:
  Package python-simplejson is not configured yet.
 python-lazr.restfulclient depends on python-wadllib (>= 1.1.4); however:
  Package python-wadllib is not configured yet.
 python-lazr.restfulclient depends on python-oauth; however:
  Package python-oauth is not configured yet.


dpkg: error processing package python-lazr.restfulclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-launchpadlib:
 python-launchpadlib depends on python-httplib2 (>= 0.4.0); however:
  Package python-httplib2 is not configured yet.
 python-launchpadlib depends on python-keyring (>= 0.5); however:
  Package python-keyring is not configured yet.
 python-launchpadlib depends on python-lazr.restfulclient (>= 0.11.2); however:
  Package python-lazr.restfulclient is not configured yet.
 python-launchpadlib depends on python-lazr.uri (>= 1.0.2-4~); however:
  Package python-lazr.uri is not configured yet.
 python-launchpadlib depends on python-oauth; however:
  Package python-oauth is not configured yet.
 python-launchpadlib depends on python-simplejson; however:
  Package python-simplejson is not configured yet.
 python-launchpadlib depends on python-wadllib; however:
  Package python-wadllib is not configured yet.


dpkg: error processing package python-launchpadlib (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing package python-lxml (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-defer (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of python-aptdaemon:
 python-aptdaemon depends on python-apt (>= 0.8.5~ubuntu1); however:
  Package python-apt is not configured yet.
 python-aptdaemon depends on python-debian; however:
  Package python-debian is not configured yet.
 python-aptdaemon depends on python-defer; however:
  Package python-defer is not configured yet.
 python-aptdaemon depends on python-dbus; however:
  Package python-dbus is not configured yet.
 python-aptdaemon depends on python-gi; however:
  Package python-gi is not configured yet.


dpkg: error processing package python-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 1.1.1-1ubuntu5.1); however:
  Package python-aptdaemon is not configured yet.
 python-aptdaemon.gtk3widgets depends on python-gi; however:
  Package python-gi is not configured yet.


dpkg: error processing package python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing package python-dirspec (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package python-lockfile (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of sessioninstaller:
 sessioninstaller depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
 sessioninstaller depends on python-commandnotfound; however:
  Package python-commandnotfound is not configured yet.
 sessioninstaller depends on python-defer; however:
  Package python-defer is not configured yet.
 sessioninstaller depends on python-gi; however:
  Package python-gi is not configured yet.


dpkg: error processing package sessioninstaller (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libglib2.0-dev
 lsb-release
 python-apt
 python-cairo
 python-chardet
 python-commandnotfound
 python-configglue
 python-crypto
 python-cupshelpers
 python-dbus
 python-debian
 python-gi
 python-gobject-2
 python-gtk2
 python-httplib2
 python-keyring
 python-lazr.uri
 python-simplejson
 python-wadllib
 python-oauth
 python-lazr.restfulclient
 python-launchpadlib
 python-lxml
 python-defer
 python-aptdaemon
 python-aptdaemon.gtk3widgets
 python-dirspec
 python-lockfile
 sessioninstaller
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by schragge on 2014-12-24
Ouch. python is already installed by default on *any* Ubuntu system. It's 14.04 LTS (trusty) if I'm not mistaken.

Well let's start with
```

sudo apt-get --reinstall --only-upgrade ^python
sudo dpkg --configure -a
sudo apt-get -f install

```

---

