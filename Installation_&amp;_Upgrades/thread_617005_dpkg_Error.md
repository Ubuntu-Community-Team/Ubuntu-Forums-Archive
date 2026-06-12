---
title: "dpkg Error"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by Arcuru on 2007-11-18
After recently upgrading, I was prompted to manually run "dpkg --configure -a" and it didn't resolve the issue.  I'm fairly new so I'm not sure how to fix it.  Any ideas?

The output of sudo dpkg --configure -a is below.

~$ sudo dpkg --configure -a
Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libIlmImf.so.2 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libkmedia2_idl.so.1 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libmcop.so.1.0.0 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/liblua50.so.5 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libgmcop.so.1.0.0 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libsoundserver_idl.so.1 is not an ELF file - it has the wrong magic bytes at the start.

Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135

---

### Post by Pumalite on 2007-11-19
Try:
sudo dpkg --remove --force-remove-reinstreq <packagename>
sudo apt-get update
sudo apt-get upgrade

---

