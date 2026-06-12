---
title: "coreutils package won't upgrade"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by mrhaffer on 2006-11-07
Not abble to upgrade coreutils.  Suspect old version is corrupted during recovery process from incomplete dapper upgrade.  Get following errors:

Preparing to replace coreutils 5.2.1-2ubuntu2 (using .../coreutils_5.93-5ubuntu4_i386.deb) ...
Removing `local diversion of /usr/share/man/man1/md5sum.textutils.1.gz to /usr/share/man/man1/md5sum.1.gz'
dpkg-divert: rename involves overwriting `/usr/share/man/man1/md5sum.textutils.1.gz' with
  different file `/usr/share/man/man1/md5sum.1.gz', not allowed
dpkg: error processing /var/cache/apt/archives/coreutils_5.93-5ubuntu4_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/coreutils_5.93-5ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I delete old version and install new?

---

### Post by mrhaffer on 2006-11-09
Not able to resolve this issue.  Attempted upgrade to 6.10.  Now have new problem with Samba not installing and broken.  Something "dangling" in older version.  Will attempt apt-get --purge remove

---

