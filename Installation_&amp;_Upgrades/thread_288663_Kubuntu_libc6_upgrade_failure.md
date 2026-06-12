---
title: "Kubuntu libc6 upgrade failure"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by ReetP on 2006-10-30
Trying to do an upgrade and get the following error. Anyone have any ideas on how to get round this ?

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 101758 files and directories currently installed.)
Preparing to replace libc6 2.3.5-1ubuntu12 (using .../libc6_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb (--unpack):
unable to make backup link of `./usr/share/zoneinfo/America/Danmarkshavn' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

