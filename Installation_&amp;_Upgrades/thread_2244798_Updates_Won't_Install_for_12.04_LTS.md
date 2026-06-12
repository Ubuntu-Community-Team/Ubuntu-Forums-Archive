---
title: "Updates Won't Install for 12.04 LTS"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2014-09-18
12.04 LTS on my server.
9 updates won't install. Keeps saying "Requires installation of untrusted packages" and the only option is to close the dialog. Seems to be an endless loop as I've tried clicking over 9 times and even unselected all but one update and only the Chrome update as well and nothing installs, but keeps returning to the "untrusted packages" dialog.

Details:  "apport apport-gtk gnome-control-center gnome-control-center-data google-chrome-stable libgnome-control-center1 python-apport python-problem-report rsyslog"

Changes for the 1st update:
[I]Changes for the versions:
Installed version: 2.0.1-0ubuntu17.6
Available version: 2.0.1-0ubuntu17.7

Version 2.0.1-0ubuntu17.7: 

  * fix up apport reporting for linux-lts-raring kernels (LP: #1352829)
    - add links for linux-lts-trusty to the package to map those to
      the source_linux.py hooks.
[/I]

---

### Post by ibjsb4 on 2014-09-18
For untrusted packages:

[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

Apport:

[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

---

### Post by HDTimeshifter on 2014-09-19
Method 1 for untrusted packages worked.
Thanks!

---

### Post by HDTimeshifter on 2014-09-19
Can't delete posts?

---

