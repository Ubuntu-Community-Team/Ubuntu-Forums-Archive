---
title: "dpkg errors"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by FredPiano on 2006-10-05
I have a ThinkPad Z61m running Edgy.  I did a dist-upgrade, and this is what happens:

jonathan@edgy:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  dvdrip
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
12 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-gobject (2.12.2-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 281, in ?
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 154, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 121, in install_modules_func
    raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Trying to overwrite pygtk.py which is already provided by /usr/share/python-support/python-gtk
dpkg: error processing python-gobject (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-gobject (>= 2.12.1); however:
  Package python-gobject is not configured yet.
dpkg: error processing python-gtk2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-glade2:
 python-glade2 depends on python-gtk2 (= 2.10.3-0ubuntu3); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-glade2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on python-gtk2 (>= 2.6); however:
  Package python-gtk2 is not configured yet.
 alacarte depends on python-glade2 (>= 2.6); however:
  Package python-glade2 is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
 apport-gtk depends on python-glade2; however:
  Package python-glade2 is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
 deskbar-applet depends on python-glade2; however:
  Package python-glade2 is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-device-manager:
 hal-device-manager depends on python-glade2; however:
  Package python-glade2 is not configured yet.
dpkg: error processing hal-device-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
 language-selector depends on python-glade2; however:
  Package python-glade2 is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing onboard (--configure):
 dependency problems - leaving unconfigured
Setting up python-mmpython (0.4.9-1build1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/mmpython/video/__init__.py
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/mmpython/video/__init__.py
dpkg: error processing python-mmpython (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on alacarte; however:
  Package alacarte is not configured yet.
 ubuntu-desktop depends on apport-gtk; however:
  Package apport-gtk is not configured yet.
 ubuntu-desktop depends on deskbar-applet; however:
  Package deskbar-applet is not configured yet.
 ubuntu-desktop depends on hal-device-manager; however:
  Package hal-device-manager is not configured yet.
 ubuntu-desktop depends on language-selector; however:
  Package language-selector is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python-glade2; however:
  Package python-glade2 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-gobject
 python-gtk2
 python-glade2
 alacarte
 apport-gtk
 deskbar-applet
 hal-device-manager
 language-selector
 onboard
 python-mmpython
 ubuntu-desktop
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)


I think the root of the problem is python-gobject.  The same thing was happening with python-gtk2 for a week or so.

Thanks

---

