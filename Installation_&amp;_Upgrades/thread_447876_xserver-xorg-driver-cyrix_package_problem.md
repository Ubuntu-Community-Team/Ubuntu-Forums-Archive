---
title: "xserver-xorg-driver-cyrix package problem"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by scapps on 2007-05-18
Greetings,

When updating from Edgy to Feisty (AMD64 laptop, nvidia video), I am running into a problem:

824 upgraded, 49 newly installed, 8 to remove and 0 not upgraded.
Need to get 0B/738MB of archives.
After unpacking 320MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg-query: parse error, in file `/var/lib/dpkg/available' near line 17779 package `xserver-xorg-driver-cyrix':
 field name `u' must be followed by colon
exim4-config.postinst: [WARN] Installed debconf version is broken. Aborting preconfigure.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 17779 package `xserver-xorg-driver-cyrix':
 field name `u' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

Is there any way around this?

Thanks.

---

