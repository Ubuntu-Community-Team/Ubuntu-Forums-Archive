---
title: "package dependencies cannot be resolved"
date: 2014-09-22
forum: Installation &amp; Upgrades
---

### Post by thomasjb on 2014-09-22
The following packages have unmet dependencies:

linux-image-extra-3.13.0-35-generic: Depends: linux-image-3.13.0-35-generic but it is not installed
linux-image-extra-3.13.0-36-generic: Depends: linux-image-3.13.0-36-generic but it is not installed
linux-image-generic: Depends: linux-image-3.13.0-36-generic but it is not installed

...tried holding the package(s) but that doesn't seem to help.  I am fairly new to Ubuntu....just upgraded from 12.04 with a fresh install of 14.04 on a Dell Latitude D505 with 2 gm ram, dual booting with Windows XP

Please help...much appreciated.

user:  thomasjb
email: [email]thomasjb@yahoo.com[/email]

---

### Post by TheFu on 2014-09-23
Try using **aptitude**. It is much, much smarter about dependencies. I use it anywhere apt-get would normally be used.

---

