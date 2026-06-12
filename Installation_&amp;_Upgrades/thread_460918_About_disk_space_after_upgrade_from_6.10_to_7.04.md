---
title: "About disk space after upgrade from 6.10 to 7.04"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by ema on 2007-06-01
Hi guys if I do the upgrade from 6.10 to 7.04 I notice that many files are downloaded. Once done the download (approx 700 mb) and the upgrade is executed, what do happens to these files?
Do i need to *waste* 700 mbs or after upgrade are that files removed from disk?

Thanks in advance,
Ema! :-)

---

### Post by epiphiny on 2007-06-01
I'm fairly sure that these files are not deleted per se, as they should replace your existing files.  I did see a small incease in disk useage, but this was mainly due to knew and shiny apps being added.

---

### Post by openmtl on 2007-06-01
See the apt-get clean option in the man pages. The packages are temporarily stored in /var/cache/apt/archives/ and  /var/cache/apt/archives/partial/ and clean clears these out other than the lock file. If apt is used as dselect then this clean is done automatically. Truthfully I haven't checked my system at all for many months to see if that space is really clear so just quoting man pages right now and my gut feel that df -k hasn't shifted around much so it must be working after the 6.10 - 7.04 upgrade.

---

### Post by ema on 2007-06-01
Ok very good...Indeed if there's a used space increase of some MB is fine because of new shiny apps.

So thanks, I'll update,
Ema! :-)

---

