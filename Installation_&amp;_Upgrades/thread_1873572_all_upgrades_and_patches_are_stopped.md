---
title: "all upgrades and patches are stopped"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by ixguy on 2011-11-01
Hi all.

When upgrading from 11.04 to 11.10 the upgrade-process stopped. 
It reported problems with replacing libmono-cairo2.0-cil. The rest of the upgrade stopped and the error-message I receive is listed below.

I`ve rebooted the machine several times and apt-get are unable to install any package due to issues replacing the libmono-cairo package.

Any idea what this might be?

-------



Preparing to replace libmono-cairo2.0-cil 2.6.7-5ubuntu3 (using .../libmono-cairo2.0-cil_2.10.5-1_all.deb) ...
Unpacking replacement libmono-cairo2.0-cil ...
dpkg: error processing /var/cache/apt/archives/libmono-cairo2.0-cil_2.10.5-1_all.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/libmono-cairo2.0-cil_2.10.5-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ixguy on 2011-11-02
*bump*

---

