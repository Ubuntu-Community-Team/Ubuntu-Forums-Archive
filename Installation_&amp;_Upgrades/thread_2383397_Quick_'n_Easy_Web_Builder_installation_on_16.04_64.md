---
title: "Quick 'n Easy Web Builder installation on 16.04 64-bit -- can it be done?"
date: 2018-01-24
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2018-01-24
Developer of software claims successful installation of software requires  installation of libgtk2.0-0:i386 (or some related packages).  However, attempting installation of libgtk2.0-0:i386 fails with numerous dependency issues.

How do I install Quick 'n Easy Web Builder?  I have tried current versions as well as earlier versions.

Thank you,

John

---

### Post by QIII on 2018-01-24
Hello!

Could you attempt to install from the terminal and post back the entirety of the results in code tags?

---

### Post by cigtoxdoc on 2018-01-24
Please see below:

```
johnl@johnl-Vostro-3500:~/Downloads$ sudo dpkg -i quick-n-easy-web-builder-5_5.2.4_i386.deb
[sudo] password for johnl: 
(Reading database ... 503887 files and directories currently installed.)
Preparing to unpack quick-n-easy-web-builder-5_5.2.4_i386.deb ...
Unpacking quick-n-easy-web-builder-5:i386 (5.2.4) over (5.2.4) ...
dpkg: dependency problems prevent configuration of quick-n-easy-web-builder-5:i386:
 quick-n-easy-web-builder-5:i386 depends on libcairo2 (>= 1.6.0).
 quick-n-easy-web-builder-5:i386 depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0:i386 is not installed.
 quick-n-easy-web-builder-5:i386 depends on libgtk2.0-0 (>= 2.24.0); however:
  Package libgtk2.0-0:i386 is not installed.
 quick-n-easy-web-builder-5:i386 depends on libpango1.0-0 (>= 1.18.0); however:

dpkg: error processing package quick-n-easy-web-builder-5:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 quick-n-easy-web-builder-5:i386
johnl@johnl-Vostro-3500:~/Downloads$
```

---

