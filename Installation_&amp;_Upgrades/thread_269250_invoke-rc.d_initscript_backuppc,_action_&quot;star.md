---
title: "invoke-rc.d: initscript backuppc, action &quot;start&quot; failed."
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by gmillikan on 2006-10-01
Trying to install SAMBA using "sudo apt-get install samba smbfs" but I'm getting the below errors.  Any tips on how can I resolve these errors?

---

### Post by dcstar on 2006-10-21
> **gmillikan said:**
> Trying to install SAMBA using "sudo apt-get install samba smbfs" but I'm getting the below errors.  Any tips on how can I resolve these errors?

You didn't seem to post any errors.

I just tried to install backuppc on my Breezy box but it wouldn't install.

**Finally** found out that the install depended on the **wwwconfig-common** package, but it was too stupid to check that it was already there.

I have put in a bug report as I hope others won't waste their time with this (as I did).

---

