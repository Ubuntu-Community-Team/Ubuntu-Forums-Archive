---
title: "xserver-xorg-core fails to upgrade"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by pean on 2008-06-17
I manually run apt-get to fetch and install applications and upgrades. I've currently have to uninstalled upgrades: tzdata and xserver-xorg-core.

When running upgrade I get this error:

```
(Reading database ... dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.3.0.0.dfsg-12ubuntu8.4_amd64.deb (--unpack):
 files list file for package `xserver-xorg-core' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg-core_2%3a1.3.0.0.dfsg-12ubuntu8.4_amd64.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I think this might be related to why I no longer can get any output on the screen, it goes black right after Grub.. I've search forums, but have not find any answer or similar problems.

I have a Nvidia GeForce 8600 GT graphics card. I have not had any problems with this setup until now.

---

### Post by pean on 2008-06-17
[This post]("http://ubuntuforums.org/showpost.php?p=1635843&postcount=9") solved it.

---

