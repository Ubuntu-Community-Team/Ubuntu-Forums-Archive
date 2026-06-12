---
title: "ipaudit installation"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by jls_ks on 2006-11-01
I am trying to get ipaudit running on latest Ubuntu version.

I have attempted the install, but cannot get the configure script to build the make files.

I also found ipaudit-0-95 on site [http://ubuntu.cbn.net.id/Ubuntu/packages/net-mgmt/](http://ubuntu.cbn.net.id/Ubuntu/packages/net-mgmt/) but have not been able to figure out how to get this tbz file to work, or how to add this into the sources.list such that apt-get could use it, if that is possible.

There is a Debian package available, but not sure if I can use this or not.

I am relatively new to Ubuntu, and not a high end user on linux in general, so any help would be greatly appreciated.

Thanks

---

### Post by jls_ks on 2006-11-01
Well I tried the Debian package, but get libpcap0 dependency issue. Even though libpcap0.8 is installed.:(

---

### Post by ahathaway on 2007-03-27
I just noticed that you were having dependency issues with the IPAudit install with Ubuntu.  In order to install IP audit you will need to install libpcap.so.0.7 for it to work.  Ubuntu comes with libpcap.so.0.8 and that does not work with IPAudit.  Good luck!

---

