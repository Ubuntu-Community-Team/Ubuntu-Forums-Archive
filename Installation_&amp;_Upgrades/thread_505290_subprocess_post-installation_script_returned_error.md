---
title: "subprocess post-installation script returned error exit status 139"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by amli801 on 2007-07-20
Hello, this is my first post and i've been using ubuntu 7.04 on my laptop  for 3 months now, for some stupid reason i did a fresh install on my acer aspire 5050 and i get a lot of subprocess error..which i didnt have this problem during my first installation. Here's what my terminal show when i did  ' sudo dpkg --configure -a ' 

```
amli@Acer-5052ANWXMi:~$ sudo dpkg --configure -a
Setting up capplets-data (2.18.1-0ubuntu2.1) ...

(update-desktop-database:6581): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up python2.5 (2.5.1-0ubuntu1) ...

(update-desktop-database:6598): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing python2.5 (--configure):
 subprocess post-installation script returned error exit status 139
Setting up python2.4 (2.4.4-2ubuntu7) ...

(update-desktop-database:6613): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing python2.4 (--configure):
 subprocess post-installation script returned error exit status 139
Setting up openoffice.org-math (2.2.0-1ubuntu4) ...

(update-desktop-database:6621): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-math (--configure):
 subprocess post-installation script returned error exit status 139
Setting up openoffice.org-draw (2.2.0-1ubuntu4) ...

(update-desktop-database:6629): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-draw (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gparted (0.2.5-2ubuntu2) ...

(update-desktop-database:6634): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gparted (--configure):
 subprocess post-installation script returned error exit status 139
Setting up openoffice.org-calc (2.2.0-1ubuntu4) ...

(update-desktop-database:6642): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-calc (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...

(update-desktop-database:6662): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of python-all:
 python-all depends on python2.4; however:
  Package python2.4 is not configured yet.
 python-all depends on python2.5; however:
  Package python2.5 is not configured yet.
dpkg: error processing python-all (--configure):
 dependency problems - leaving unconfigured
Setting up openoffice.org-common (2.2.0-1ubuntu4) ...
Updating OpenOffice.org's dictionary list... done.

(update-desktop-database:6674): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python2.5; however:
  Package python2.5 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on python2.5 (>= 2.5); however:
  Package python2.5 is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-math; however:
  Package openoffice.org-math is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python:
 python depends on python2.5 (>= 2.5.1); however:
  Package python2.5 is not configured yet.
dpkg: error processing python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python (>= 2.4); however:
  Package python is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gdbm:
 python-gdbm depends on python (<< 2.6); however:
  Package python is not configured yet.
 python-gdbm depends on python (>= 2.4); however:
  Package python is not configured yet.
dpkg: error processing python-gdbm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-common:
 hwdb-client-common depends on python; however:
  Package python is not configured yet.
dpkg: error processing hwdb-client-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python2.5; however:
  Package python2.5 is not configured yet.
 update-manager-core depends on python (<< 2.6); however:
  Package python is not configured yet.
 update-manager-core depends on python (>= 2.4); however:
  Package python is not configured yet.
dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wifi-radar:
 wifi-radar depends on python; however:
  Package python is not configured yet.
dpkg: error processing wifi-radar (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on python; however:
  Package python is not configured yet.
dpkg: error processing unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-problem-report:
 python-problem-report depends on python (>= 2.4); however:
  Package python is not configured yet.
dpkg: error processing python-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-gnome:
 hwdb-client-gnome depends on hwdb-client-common (>= 0.6-0ubuntu23); however:
  Package hwdb-client-common is not configured yet.
dpkg: error processing hwdb-client-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ndisgtk:
 ndisgtk depends on python (>= 2.5); however:
  Package python is not configured yet.
 ndisgtk depends on python (<< 3); however:
  Package python is not configured yet.
dpkg: error processing ndisgtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gimp-python:
 gimp-python depends on python (>= 2.5); however:
  Package python is not configured yet.
 gimp-python depends on python (<< 2.6); however:
  Package python is not configured yet.
dpkg: error processing gimp-python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on python-uno (>= 2.2.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python (>= 2.4); however:
  Package python is not configured yet.
 apport depends on python-apport (>= 0.43); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python (>= 2.4); however:
  Package python is not configured yet.
 apport-gtk depends on python-apport (>= 0.45); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on python (>= 2.4); however:
  Package python is not configured yet.
 gnome-app-install depends on python-gdbm; however:
  Package python-gdbm is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-alsaaudio:
 python-alsaaudio depends on python (<< 2.6); however:
  Package python is not configured yet.
 python-alsaaudio depends on python (>= 2.4); however:
  Package python is not configured yet.
dpkg: error processing python-alsaaudio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 capplets-data
 python2.5
 python2.4
 openoffice.org-math
 openoffice.org-draw
 gparted
 openoffice.org-calc
 gnome-panel-data
 python-all
 openoffice.org-common
 update-manager
 python-uno
 openoffice.org
 openoffice.org-java-common
 openoffice.org-impress
 gnome-panel
 python
 python-apport
 python-gdbm
 openoffice.org-base
 hwdb-client-common
 update-manager-core
 openoffice.org-filter-mobiledev
 wifi-radar
 unattended-upgrades
 python-problem-report
 hwdb-client-gnome
 ndisgtk
 gimp-python
 openoffice.org-writer
 apport
 openoffice.org-evolution
 apport-gtk
 gnome-app-install
 python-alsaaudio

```

Anyone else having the same problem? a solution would be nice :) Thank you in advance.

---

### Post by kagashe on 2007-07-20
Check the integrity of the CD.

kagashe

---

### Post by amli801 on 2007-07-20
Do you mean by checking the md5sum ?

---

### Post by kagashe on 2007-07-20
> **amli801 said:**
> Do you mean by checking the md5sum ?No. When you boot with the CD scroll down to the item which states for checking of CD integrity and press enter.

kagashe

---

### Post by amli801 on 2007-07-20
checked. and the result is no errors..any ideas?
[edit] It appears that i can install a couple of software such as GNUCASH and others office applications. But at the end of each installation, the subprocess error like the above keep popping out, but the software was installed properly and running properly too..
I have done the update for ubuntu and the kernel, so its the latest. Still couldnt solve the problem. I have tried to fresh install ubuntu for 3 times so im tired to wait around 4 hours for another installation again...If someone could just point out where i did wrong..

---

### Post by amli801 on 2007-07-20
Bump-bump-bump

---

### Post by kagashe on 2007-07-21
> **amli801 said:**
> checked. and the result is no errors..any ideas?
[edit] It appears that i can install a couple of software such as GNUCASH and others office applications. But at the end of each installation, the subprocess error like the above keep popping out, but the software was installed properly and running properly too..
I have done the update for ubuntu and the kernel, so its the latest. Still couldnt solve the problem. I have tried to fresh install ubuntu for 3 times so im tired to wait around 4 hours for another installation again...If someone could just point out where i did wrong..
If every software gets installed and runs properly why do you worry for the errors?

kagashe

---

### Post by amli801 on 2007-07-23
Its annoying, haha..Did a couple of research on the net, and some said it was because of broken dependencies or something, not quite sure though. I'll try to get rid of it somehow then ..thanks again.

---

### Post by zanglang on 2007-07-24
> **kagashe said:**
> If every software gets installed and runs properly why do you worry for the errors?

kagashe

Actually I think there are some *serious* problems with his apt, it's definitely *not* installing properly... Is openoffice working for you, amli801?

---

### Post by amli801 on 2007-07-27
Yea, openoffice is fine, its just that the errors keep popping out after the end of installation. It was Feisty 7.04 i386.. I did another fresh install with a Feisty 7.04 AMD 64 since im using a AMD Turion 64 processor..and it work out fine, no more errors..

---

