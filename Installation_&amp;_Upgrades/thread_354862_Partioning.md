---
title: "Partioning"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by derekdb on 2007-02-06
I loaded Ubuntu from CDROM and started install on C: It showed 50% partition and the mouse showed progress.  There ir hung for two hours until aborted.  Hard disk remained unpartitiioned.   Plenty of Ram and CPU spped.. 80Ghz HD

---

### Post by mikewhatever on 2007-02-06
Since you've mentioned C, I assume you have a version of Windows installed, and that you were trying to resize the C partition. Something similar happened to me too. The installer was unable to resize the partition, until the DSKCHK check was run on it from Windows. After the check, the resize operation took 10 seconds. To run the check from Windows, open My Computer, right click on C, chose properties. Go to Tools tab and click Check Now button.
Defragment the partition, unless you haven't.

Good Luck):P

---

