---
title: "cannot update to 13.10"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by ELD on 2013-10-17
It seems something is holding back my upgrade to ubuntu 13.10, bug report is here: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1240988](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1240988)

Looks like it might be broken packages: [https://launchpadlibrarian.net/153986687/VarLogDistupgradeAptlog.txt](https://launchpadlibrarian.net/153986687/VarLogDistupgradeAptlog.txt)

Haven't a clue how to fix it.

---

### Post by david98 on 2013-10-17
I had the same problem so in the end went for a fresh install via usb drive everything's working fine now

---

### Post by oldos2er on 2013-10-17
The answer is in post #2 of [https://bugs.launchpad.net/ubuntu/+s...r/+bug/1240988]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1240988"), disable the xorg-edgers PPA.

---

