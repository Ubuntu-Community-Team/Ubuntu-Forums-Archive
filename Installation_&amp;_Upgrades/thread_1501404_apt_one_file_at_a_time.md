---
title: "apt: one file at a time"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by cong06 on 2010-06-04
Aptitude and apt-get have a thing where they like to download more then one file at a time, maybe 2, maybe 3.

Is there a way to have these programs only download one at a time?
It'd help my unstable connection if these downloads would actually finish...

---

### Post by telewatho on 2010-06-04
Hmmm, interesting.  Don't know there's an option for that.  Each package should be one file, so if you only select one package to download at once, it should be ok.  However, the package lists themselves come from multiple locations.....:-k

---

### Post by cong06 on 2011-03-17
I switched to apt-cacher-ng which solved this problem. The files stay partly downloaded and don't re-download any part of the file.

So if the connection dies, the part that was downloaded isn't wasted.

---

