---
title: "missing file &quot;tzdata_2007h-0ubuntu0.7.10_all.deb&quot; installing 7.10"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by aag_ubu on 2007-10-20
Hi,

I-ve tried to update from 7.04 to 7.10 and I get the following error message:

Failed to fetch: 
http:// es.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007h-0ubuntu0.7.10_all.deb 
404 Not Found

The file is missing in "http://es.archive.ubuntu.com" although it exists in "http://archive.ubuntu.com"

Any suggestion?, can I change the installation source to archive.ubuntu.com or should I wait until they fix this problem in the "es.archive.ubuntu.com" server? I have this doubt because the "es" is supposed to be for "spanish" downloads, and I don't know if I can have problems using the other server.

---

### Post by denham2010 on 2007-10-20
I have updated 2 machines today, and prior to doing the distribution upgrade, there has been an update to tz_data which is required to be done before doing the distro upgrade.

Ensure you have all the official repositories enabled and you should then get the update.

The only problems I had with both upgrades were the following:

1. If you have Beryl installed and running, stop it running before upgrading - it gets removed and replaced with compiz-fusion.

2. If you have apt-file installed, remove it before upgrading, it causes the installer to crash right at the end, after hours of downloading, leaving you with a half installed very unstable system....it took me a while to recover from that.

3. If you have any unofficial repositories enabled, disable them as they can cause the installed to crash right at the start.

4. If you have awn on your system, after the upgrade it will fail to load because the library file libwnck is upgraded. It is easily fixed by trying to run awn from a terminal and recording which version of libwnck.so is required, then creating a symlink in the same folder as the updated libwnck.so and just renaming it to the version awn requires.

Hope this helps you.

---

