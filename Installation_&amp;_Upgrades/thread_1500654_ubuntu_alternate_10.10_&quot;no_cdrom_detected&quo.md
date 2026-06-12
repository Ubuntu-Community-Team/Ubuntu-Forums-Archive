---
title: "ubuntu alternate 10.10 &quot;no cdrom detected&quot;"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by lesnoland on 2010-06-03
i downloaded today the daily-build alternate of ubuntu 10.10, it says there its bigger than a cd-image and to only use a dvd or an usb disk.

the problem is for some reason when i booted from my usb disk it said constantly that it cant find the cd-rom. even after mounting the (mkdir /dev/cdroms/;ln -s ../dev/sdb1 cdrom0) trick still nothing, it complained it can not read from CD.

anyway, what solved it was, pressing F6, and then adding the following before quiet in boot options:

cdrom-detect/try-usb=true

note: i created the usb startup disk from 9.04.

---

