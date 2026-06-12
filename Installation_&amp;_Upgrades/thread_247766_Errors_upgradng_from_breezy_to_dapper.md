---
title: "Errors upgradng from breezy to dapper"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by elinehan on 2006-08-31
The upgrade procedure from breezy to dapper recommended by the ubuntu community halted with this error and i have no idea how to correct it. Any help would be greatly appreciated.

The command I ran was: sudo apt-get update && sudo apt-get dist-upgrade (After following the other steps on the page sucessfully)

Thanks

- Eamonn

Unpacking replacement sysv-rc ...
Setting up sysv-rc (2.86.ds1-6ubuntu32) ...

(Reading database ... 56776 files and directories currently installed.)
Preparing to replace coreutils 5.2.1-2ubuntu2 (using .../coreutils_5.93-5ubuntu4_i386.deb) ...
Removing `local diversion of /usr/share/man/man1/md5sum.textutils.1.gz to /usr/share/man/man1/md5sum.1.gz'
dpkg-divert: rename involves overwriting `/usr/share/man/man1/md5sum.textutils.1.gz' with
  different file `/usr/share/man/man1/md5sum.1.gz', not allowed
dpkg: error processing /var/cache/apt/archives/coreutils_5.93-5ubuntu4_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/coreutils_5.93-5ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

