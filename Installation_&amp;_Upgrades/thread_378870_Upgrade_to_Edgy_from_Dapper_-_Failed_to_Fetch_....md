---
title: "Upgrade to Edgy from Dapper - Failed to Fetch ..."
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by jeff-- on 2007-03-07
I went to upgrade from Dapper Drake 6.06 to Edgy Eft 6.10 today.  I used the "official" method to upgrade (gksu "update-manager -c") and pressed upgrade or whatever.  It was on the first step and I get this error:

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Anybody know what I can do to fix this error and finish upgrading?

---

### Post by Kateikyoushi on 2007-03-07
Recently nobody could update via the update manager, what works is to edit the sources.list or wait till it gets fixed.

---

### Post by jeff-- on 2007-03-07
> **Kateikyoushi said:**
> Recently nobody could update via the update manager, what works is to edit the sources.list or wait till it gets fixed.Ah ok, thanks.  I assume you mean only update the OS version, because I have been able to get regular updates with the update manager.

---

### Post by Kateikyoushi on 2007-03-07
Indeed regular updates work but version upgrades failed recently, I had to go the sources.list way as well.

---

### Post by jeff-- on 2007-03-27
Is the update manager for version upgrades still not working properly?  I am getting a similar error, this time "Sub-process gzip returned an error code (1)" from a noreply.org address.

---

