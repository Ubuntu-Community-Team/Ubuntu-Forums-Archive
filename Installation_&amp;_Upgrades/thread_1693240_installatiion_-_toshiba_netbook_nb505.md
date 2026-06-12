---
title: "installatiion - toshiba netbook nb505"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by Erewhonman on 2011-02-22
Tried loading 10.04 from a disk I had used for installation on previous acer laptop using an external dvd-cd reader. Nada! Toshiba will not read it whether tried normally or on booting. Then tried download from wubi on several occasions and different ways.  It seems Toshiba iso does not work.  Am I paranoid or has Toshiba/Windows contrived to make changeover impossible?  Suggestions?

---

### Post by bcbc on 2011-02-22
If you're using wubi.exe from [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) there's a [bug]("https://bugs.launchpad.net/wubi/+bug/722955") and it won't work.
If you're running wubi from an Ubuntu dvd image it won't work either.

If not, then post the log file found in the %temp% directory.

---

