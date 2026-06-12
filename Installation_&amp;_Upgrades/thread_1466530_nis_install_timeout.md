---
title: "nis install timeout"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by tomhorsley on 2010-04-30
My ypserver is on a different subnet. As I was just reminded while installing my new 10.04 KVMs, I have to sit around and timeout forever when I install the "nis" package because the package asks for domain, but doesn't allow me to specify ypserver. It clearly ain't gonna find it with a broadcast, but it takes forever for it to figure that out. Is there any way to avoid this timeout? (Like maybe filling in the /etc/yp.conf file before installing nis). Or is there maybe some chance the nis installation could be changed so I can specify the ypserver?

---

