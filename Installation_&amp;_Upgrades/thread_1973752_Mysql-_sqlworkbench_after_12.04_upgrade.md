---
title: "Mysql- sqlworkbench after 12.04 upgrade"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by EvansFive on 2012-05-05
I successfully upgraded 11.10 to 12.04 and installed MySQL-workbench.....

But each time I try to use it stops responding any crashes

Any suggestions how I can fix this please?

Thanks
Peter

---

### Post by mbrennwa on 2012-05-08
> **EvansFive said:**
> I successfully upgraded 11.10 to 12.04 and installed MySQL-workbench.....

But each time I try to use it stops responding any crashes

Any suggestions how I can fix this please?

Thanks
Peter

Try reinstalling MySQL. I (and many others) had issues with MySQL, which stopped working after upgrading to Ubuntu 12.04. Reinstallation of mysql did the trick in my case, and all databases were still there and in good health.

Matthias

---

### Post by helotbc on 2012-05-14
Thanks Matthias.  Reinstalled mysql server and mysql client from Ubuntu Software Center and that fixed me up.  -Brendan

---

