---
title: "Broken Upgrade: Dumps into BusyBox after Segfaulting like crazy"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by krymson on 2006-11-15
After upgrading from Breezy to Dapper through the method of modifying the sources.lst and doing the apt-get install upgrade thingy, everything seemed to work fine. I upgraded some packages, mainly just Xine and Totem.

Unfortunately the next time I restarted, the system that was working perfectly before, stopped booting up normally. Right after "Uncompressing Linux Kernel", I get:
Segmentation Fault
Segmentation Fault
...

/dev/mapper/Ubuntu-root does not exist. Dropping to Shell!
...
/bin/sh can't access tty: job control turned off

---------------------------------

Is there anyway I can recover this installation? Or can I install a new one on top of this one without destroying the data?

---

