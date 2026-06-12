---
title: "unable to replace libmono-cairo2.0-cil"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by ixguy on 2011-10-27
Hi all.

When upgrading to ubuntu 11.10, I get an error in the upgrade-process because of issues with replacing libmono-cairo2.0-cil

Error message I get: 

Preparing to replace libmono-cairo2.0-cil 2.6.7-5ubuntu3 (using .../libmono-cairo2.0-cil_2.10.5-1_all.deb) ...
Unpacking replacement libmono-cairo2.0-cil ...
dpkg: error processing /var/cache/apt/archives/libmono-cairo2.0-cil_2.10.5-1_all.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Operation not permitted

**When trying to remove and purge the package I get: **

dpkg: error processing libmono-cairo2.0-cil (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 libmono-cairo2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone else experienced the same? 
Or clues on how to fix?


This is really annoying and I can`t receive any more security updates until this is fixed...


br

Ixguy

---

