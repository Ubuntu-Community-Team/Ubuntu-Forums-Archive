---
title: "Problem with dist-upgrade"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by mohaham on 2005-10-16
When i try to dist-upgrade to Breezy I get the following error:

Unpacking xkeyboard-config (from .../xkeyboard-config_0.6-5_all.deb) ...
dpkg: error processing /var/cache/apt/archives/xkeyboard-config_0.6-5_all.deb (--unpack):
 trying to overwrite `/etc/X11/xkb/rules/xorg.lst', which is also in package xlibs
Errors were encountered while processing:
 /var/cache/apt/archives/xkeyboard-config_0.6-5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


i get the same error on running this command:
apt-get -f install

Did anyone run into a similar issue..please help.

---

### Post by mohaham on 2005-10-16
this appears to get resolved by following these steps:

sudo dpkg  -i --force-overwrite --ignore-depends=xorg-common  /var/cache/apt/archives/xkeyboard-config_0.6-5_all.deb

sudo apt-get -f install

sudo apt-get dist-upgrade

---

