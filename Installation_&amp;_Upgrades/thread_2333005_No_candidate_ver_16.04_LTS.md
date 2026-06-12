---
title: "No candidate ver 16.04 LTS"
date: 2016-08-06
forum: Installation &amp; Upgrades
---

### Post by zkab on 2016-08-06
I tried to upgrade server Ubuntu 15.10 to 16.04 LTS with 'sudo do-release-upgrade' but it failed:

No candidate ver:  libapt-inst1.5
No candidate ver:  libapt-pkg4.12
No candidate ver:  libboost-iostreams1.55.0
No candidate ver:  libcwidget3
No candidate ver:  libhogweed2
No candidate ver:  libicu52
No candidate ver:  libllvm3.6
No candidate ver:  libnettle4
No candidate ver:  libsigc++-2.0-0c2a
No candidate ver:  libxapian22

What is wrong ?

---

### Post by grahammechanical on 2016-08-06
> Server / Command line Upgrade
sudo aptitude install update-manager-core
sudo do-release-upgrade

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

Did you install update-manager-core? Are those packages part of the default install of Ubuntu server? They may have come from an application that has not been upgraded to 16.04.

Regards.

---

### Post by zkab on 2016-08-08
Yes, update-manager-core is installed but I discovered that 'tvheadend' was not supported for 16.04

---

