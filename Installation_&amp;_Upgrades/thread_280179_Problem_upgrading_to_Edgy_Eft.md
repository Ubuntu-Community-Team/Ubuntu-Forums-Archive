---
title: "Problem upgrading to Edgy Eft"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by kloy1334 on 2006-10-19
I just tried to upgrade from 6.04 to 6.10, as the RC files should've been put up online already. Unfortunately, I've been receiving an error concerning x11-common, what can I do about this?

```

678 packages upgraded, 111 newly installed, 1 downgraded, 50 to remove and 6 not upgraded.
Need to get 0B/475MB of archives. After unpacking 213MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 91458 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu5_i386.deb) ...
Unpacking replacement x11-common ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man5/Xsession.5.gz', which is also in package xinit
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libxdmcp6:
 libxdmcp6 depends on x11-common (>= 1:7.0.0); however:
  Version of x11-common on system is 7.0.0-0ubuntu45.
dpkg: error processing libxdmcp6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xutils-dev:
 xutils-dev depends on x11-common (>= 1:7.0.0); however:
  Version of x11-common on system is 7.0.0-0ubuntu45.
dpkg: error processing xutils-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xutils:
 xutils depends on xutils-dev; however:
  Package xutils-dev is not configured yet.
dpkg: error processing xutils (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxdmcp6
 xutils-dev
 xutils

```

---

