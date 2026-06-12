---
title: "Live Installer File System called &quot;dont_use&quot;"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by mikebravo on 2007-12-10
Doing 'learn as you go' installing Fiesty on my new PC. Right now playing with partition schemes on live installer. When you select MANUAL install you allocate space, assign a mount point and designate a file system e.g. ext3, swap, or fat32. On the drop down list of file systems you also get a "   dont_use   " option.  What is that for and how do you use it? Every time I select   dont_use  the partitioning crashes.  Surely it is there for a reason.

---

### Post by markusf21 on 2007-12-10
this is just a guess but I think it's probably something that didn't get finished. Besides it clearly says do not use. So don't use it.

---

### Post by tripleee on 2008-04-11
Actually it's for telling the installer to not use that partition in any fashion (i.e. leave it alone).

---

### Post by cjwatson on 2008-04-11
tripleee is correct. This option had been broken for a while in the live CD installer, but I fixed it in recent daily builds and it'll work in Hardy.

---

