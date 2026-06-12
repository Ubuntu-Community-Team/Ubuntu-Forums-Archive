---
title: "Dependancy Problems in Jaunty"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by bootdoc on 2009-12-08
Having trouble configuring the following PKGS:


libdns46
 libisccfg40
 libbind9-40
 bind9-host
 dnsutils

Apparently everything depends on libdns46 and this is what I got after running:

$ sudo dpkg --configure libdns46
Setting up libdns46 (1:9.5.1.dfsg.P2-1ubuntu0.3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libdns46 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 libdns46

---

