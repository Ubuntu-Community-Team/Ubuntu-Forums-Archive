---
title: "how can i fix this?"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by Disastorm on 2006-08-16
hi can anyone tell me how to fix this.  originally my alacarte broke so i tried to reinstall it and i tried to do the same with python since i dunno it was in the error message.  somehow alacarte randomly started working again , and i havn't really had any problems but whenever i use apt-get at all i get this (after it does what I asked it to.  If i ask it to install something it will install it and then give me the following)

disastorm@Dragonball:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python2.4 (2.4.3-0ubuntu4) ...
Compiling python modules in /usr/lib/python2.4 ...
Compiling /usr/lib/python2.4/site-packages/bike/logging.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/mock.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/setpath.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/test_bikefacade.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/test_testutils.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/testall.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/testdata.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/testutils.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
dpkg: error processing python2.4 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up alacarte (0.8-0ubuntu12) ...
Compiling /usr/lib/python2.4/site-packages/bike/logging.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/mock.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/setpath.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/test_bikefacade.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/test_testutils.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/testall.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/testdata.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Compiling /usr/lib/python2.4/site-packages/bike/testutils.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
dpkg: error processing alacarte (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4-adns:
 python2.4-adns depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-adns (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-apt:
 python2.4-apt depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-cairo:
 python2.4-cairo depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-cairo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-clientcookie:
 python2.4-clientcookie depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-clientcookie (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-crypto:
 python2.4-crypto depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-crypto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-ctypes:
 python2.4-ctypes depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-ctypes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-dbus:
 python2.4-dbus depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-dictclient:
 python2.4-dictclient depends on python2.4; however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-dictclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on alacarte; however:
  Package alacarte is not configured yet.
 ubuntu-desktop depends on python2.4-dbus; however:
  Package python2.4-dbus is not configured yet.
 ubuntu-desktop depends on python2.4-dictclient; however:
  Package python2.4-dictclient is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4
 alacarte
 python2.4-adns
 python2.4-apt
 python2.4-cairo
 python2.4-clientcookie
 python2.4-crypto
 python2.4-ctypes
 python2.4-dbus
 python2.4-dictclient
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

