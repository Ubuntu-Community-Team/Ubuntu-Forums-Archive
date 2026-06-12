---
title: "Serious Dpkg issues"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by spookyct on 2007-07-04
I get tons of dpkg errors whenever i try to install anything.  It says to run dpkg --configure -a


this is the result...

```
james@james-linux-box:~$ sudo dpkg --configure -a
Password:
Setting up kde-icons-mono (3.5.6-0ubuntu1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kde-icons-mono (--configure):
 subprocess post-installation script returned error exit status 2
Setting up kdebase-data (3.5.6-0ubuntu20.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kdebase-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up capplets-data (2.18.1-0ubuntu2.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up koffice-data (1.6.2-0ubuntu1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing koffice-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gnome-app-install (0.3.31) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 2
Setting up pidgin-data (2.0.2-1~getdeb1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing pidgin-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up vlc-plugin-glide (0.8.6.release-0ubuntu4) ...
Setting up vlc-plugin-sdl (0.8.6.release-0ubuntu4) ...
Setting up vlc-plugin-alsa (0.8.6.release-0ubuntu4) ...
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.18); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.19); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up emacs21 (21.4a+1-2ubuntu1) ...
emacs-install emacs21
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/flyspell.elc
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done

dpkg: dependency problems prevent configuration of kcontrol:
 kcontrol depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kcontrol depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kcontrol (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksplash:
 ksplash depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 ksplash depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing ksplash (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksplash-engine-moodin:
 ksplash-engine-moodin depends on ksplash (>= 4:3.5.5-1); however:
  Package ksplash is not configured yet.
dpkg: error processing ksplash-engine-moodin (--configure):
 dependency problems - leaving unconfigured
Setting up kdelibs-data (3.5.6-0ubuntu14) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing kdelibs-data (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdm:
 kdm depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kdm depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of koffice-libs:
 koffice-libs depends on koffice-data (>> 1:1.6.2); however:
  Package koffice-data is not configured yet.
 koffice-libs depends on koffice-data (<< 1:1.6.3); however:
  Package koffice-data is not configured yet.
dpkg: error processing koffice-libs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kicker:
 kicker depends on kdebase-data (>> 4:3.5.6); however:
  Package kdebase-data is not configured yet.
 kicker depends on kdebase-data (<< 4:3.5.7); however:
  Package kdebase-data is not configured yet.
dpkg: error processing kicker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konqueror:
 konqueror depends on kcontrol (= 4:3.5.6-0ubuntu20.1); however:
  Package kcontrol is not configured yet.
dpkg: error processing konqueror (--configure):
 dependency problems - leaving unconfigured
Setting up apport (0.76.1) ...
 * Starting automatic crash report generation: apport                    [ OK ]
/bin/sh: Can't open gtk-update-icon-cache
dpkg: error processing apport (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdelibs-data (>= 4:3.1.4-2); however:
  Package kdelibs-data is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kexi:
 kexi depends on koffice-libs (>= 1:1.6.2); however:
  Package koffice-libs is not configured yet.
 kexi depends on koffice-libs (<< 1:1.6.3); however:
  Package koffice-libs is not configured yet.
dpkg: error processing kexi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-default-settings:
 kubuntu-default-settings depends on kdm; however:
  Package kdm is not configured yet.
 kubuntu-default-settings depends on ksplash-engine-moodin; however:
  Package ksplash-engine-moodin is not configured yet.
dpkg: error processing kubuntu-default-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on kdelibs-data (>> 4:3.5.6); however:
  Package kdelibs-data is not configured yet.
 kdelibs4c2a depends on kdelibs-data (<< 4:3.5.7); however:
  Package kdelibs-data is not configured yet.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kontact:
 kontact depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kontact (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing konsole (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libk3b2:
 libk3b2 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libk3b2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of krdc:
 krdc depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing krdc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of keep:
 keep depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing keep (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdemultimedia-kio-plugins:
 kdemultimedia-kio-plugins depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdemultimedia-kio-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkmime2:
 libkmime2 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkmime2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-common:
 adept-common depends on konsole (>= 3.5.0); however:
  Package konsole is not configured yet.
dpkg: error processing adept-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knotes:
 knotes depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing knotes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkexiv2-0:
 libkexiv2-0 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkexiv2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdenetwork-kfile-plugins:
 kdenetwork-kfile-plugins depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdenetwork-kfile-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-bin:
 kdebase-bin depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdebase-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-systemsettings:
 kde-systemsettings depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 kde-systemsettings depends on kcontrol; however:
  Package kcontrol is not configured yet.
dpkg: error processing kde-systemsettings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmailcvt:
 kmailcvt depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kmailcvt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knetworkconf:
 knetworkconf depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing knetworkconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kppp:
 kppp depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kppp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpdf:
 kpdf depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpdf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libktnef1:
 libktnef1 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libktnef1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kio-apt:
 kio-apt depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kio-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpf:
 kpf depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde3:
 python-kde3 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
 python-kde3 depends on konsole; however:
  Package konsole is not configured yet.
dpkg: error processing python-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkonq4:
 libkonq4 depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkonq4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdnssd:
 kdnssd depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdnssd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-qt:
 apport-qt depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine:
 kaffeine depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kaffeine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kate:
 kate depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of adept-updater:
 adept-updater depends on adept-common; however:
  Package adept-common is not configured yet.
 adept-updater depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing adept-updater (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kcron:
 kcron depends on kdelibs4c2a (>= 4:3.5.5-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kcron (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 kde-icons-mono
 kdebase-data
 capplets-data
 koffice-data
 gnome-app-install
 pidgin-data
 gnome-control-center
 kcontrol
 ksplash
 ksplash-engine-moodin
 kdelibs-data
 gnome-panel-data
 kdm
 koffice-libs
 kicker
 konqueror
 apport
 k3b
 kexi
 kubuntu-default-settings
 kdelibs4c2a
 kontact
 konsole
 libk3b2
 krdc
 keep
 kdemultimedia-kio-plugins
 libkmime2
 adept-common
 knotes
 apport-gtk
 libkexiv2-0
 kdenetwork-kfile-plugins
 kdebase-bin
 kde-systemsettings
 kmailcvt
 knetworkconf
 kppp
 kpdf
 libktnef1
 kio-apt
 kpf
 gnome-panel
 python-kde3
 libkonq4
 kdnssd
 apport-qt
 kaffeine
 kate
 adept-updater
 kcron
Processing was halted because there were too many errors.
james@james-linux-box:~$       
```

---

### Post by DirtDawg on 2007-07-04
Hi. Please post an example of the errors you receive when attempting to install a package normally.

---

### Post by spookyct on 2007-07-04
This happened the first time i tried to install something...

```
sujames@james-linux-box:~$ sudo aptitude install imwheel
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
james@james-linux-box:~$

```

---

### Post by madmo on 2007-07-04
I'm having the same problem!? I must confess I'm new to Ubuntu lol.

---

### Post by az on 2007-07-04
You must have mixed repositories (more than one version or distro).  Remove all the entries for one version.  Keep the latest version.

Update and then try to fix.

---

