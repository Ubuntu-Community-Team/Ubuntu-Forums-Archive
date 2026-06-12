---
title: "openssl 1.0.0a upgrade"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by bgermann on 2010-11-12
I have to upgrade my Openssl to 1.0.0a for PCI compliance. I compiled the files and installed but "Openssl version" reports back 0.8.9g instead. I have rebooted and get the same message. 
 
I have Ubuntu server 8.04 and have Parallel installed. 
 
Thanks to all that answer

---

### Post by lemming465 on 2010-11-13
This is probably a PATH issue.  The new one may have gone by default to /usr/local/bin, and probably you are getting the original version in /usr/bin.  You might want to uninstall the original (aptitude remove openssl); if that breaks stuff, re-make the new openssl with more conventional paths.

---

### Post by bgermann on 2010-11-15
Question...I'm new at the use of "Make".  My original Openssl is located inside /usr/bin/ .  The new one is installing into /usr/local/ssl/bin.  How do i install it with a more conventional path as you suggest?  I'm sure it is going to break stuff when i un-install the original version...

---

### Post by lemming465 on 2010-11-16
If you download the tarball from [www.openssl.org](www.openssl.org), you probably want to do something like:
  ./config --prefix=/usr --openssldir=/usr/lib/ssl
which regenerates Makefile from Makefile.org.

---

