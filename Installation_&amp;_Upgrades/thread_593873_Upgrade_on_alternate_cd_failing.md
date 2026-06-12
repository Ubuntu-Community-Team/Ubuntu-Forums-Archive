---
title: "Upgrade on alternate cd failing"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by hexstar on 2007-10-27
I'm trying to upgrade to gutsy but it fails with this error: [http://pastebin.com/m401be233](http://pastebin.com/m401be233) ...how do I resolve that error? Thanks! :)

---

### Post by hexstar on 2007-10-27
I resolved this issue by performing the following in terminal:


1) mount /dev/cdrom /media/cdrom

2) kdesu "sh /media/cdrom/cdromupgrade"

---

