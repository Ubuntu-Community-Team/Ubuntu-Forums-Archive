---
title: "OpenOffice not working after upgrade to 7.04"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Michel Roelofs on 2007-07-19
After upgrading Ubuntu 6.06LTS (AMD64) via 6.10 to 7.04, OpenOffice didn't work anymore, it just crashed. (I don't remember where).

Then I removed OO.o via Synaptic, reinstalled it but that gave me the same effect.

Then I selected in Synaptic "complete removal" of all OO.o packages (as far as I could find them),  reinstalled OpenOffice once more, but it crashed at the same point.

Again "complete removal" of OO.o, but then I saw that the file /usr/lib/openoffice/program/soffice.bin was still there. I removed /usr/lib/openoffice, and reinstalled it once more via Synaptic.

However, now the file /usr/lib/openoffice/program/soffice.bin is no longer present, and OpenOffice will not start due to this.

How can I fix this issue? (E.g. reinstall soffice.bin? In what package is it?)

Thanks, Michel

---

### Post by TheWizzard on 2007-07-19
upgrading is always tricky. and i'd always advice to do a clean install. 

in your situation it's even easier: backup /home and /etc folders and do a fresh install.

---

### Post by Hagar Delest on 2007-07-20
You could also try a manual install : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

