---
title: "Rollback auto updates done by v6.06"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by superba on 2006-11-17
Hi,

Is there a way to rollback an automatic update done by v6.06 about 5-7 days ago?  Apparently, that update disabled my network connection, for I can no longer contact my local network and the internet.  Ubuntu is installed on a machine that had a working copy of Win XP SP2 ++ on it and the network was fine.  In fact, it was fine with Ubuntu until the update was done.  At first I suspected ipv6, for my mickey mouse router chokes on it.  So, I disabled ipv6, I think, by blacklisting it with no effect.

Can I rollback the update?  If not, how can I fix the problem without reinstalling v6.06?

Thanks for your help.

Cheers!

---

### Post by superba on 2006-11-19
Hi,

I solved the problem in a round about way.  I upgraded to edgy eft, v6.10, and the upgrade restored my network connections thus preempting my desire to rollback the updates.

FYI, I used the official update method, <$gksu "update-manager -c">, and it worked without a hitch.

I'm still puzzled by how the update manager could access the network and download the updates when I couldn't access the network no matter what I did.

Cheers!

---

