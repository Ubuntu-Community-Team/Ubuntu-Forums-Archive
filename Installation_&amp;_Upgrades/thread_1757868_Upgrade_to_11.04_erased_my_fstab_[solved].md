---
title: "Upgrade to 11.04 erased my fstab [solved]"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by reswob on 2011-05-13
my $.02 on this upgrade:


I've been using Ubuntu since 7.04 and I've never had this happen.

I was at 10.04 and I downloaded the torrent iso of 11.04 and burned it to a CD and used that to upgrade.  I don't know if that was the problem, but doing the upgrade that way erased my fstab.  When I tried to recreate it, I was getting errors mapping to the fileshares.  Turned out the upgrade uninstalled cifs/smbfs as well. In addition to uninstalling wine. 

After reinstalling, everything is ok.... so far.  

This was NOT the smoothest upgrade.

OK.  Complaint over.

---

### Post by Quackers on 2011-05-13
I don't think upgrading 2 versions at once is considered to be a good idea. That may be why some problems occurred.

---

