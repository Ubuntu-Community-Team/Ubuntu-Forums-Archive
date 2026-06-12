---
title: "Upgrade from CD: Home Directory overwritten?"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by drx on 2005-10-14
Hello,
i have been having a lot of trouble upgrading via apt-get. I think i must have carelessly erased some repositories from my sources.list, so a lot of dependencies are broken (120 and counting) and my system only works in commandline.

So i thought about installing breezy from CD, to start with clean packages. But will my home directory be overwritten? Can i somehow save my home directory in which i have all my stuff and setup while installing from CD?

Otherwise i think i must invent something else ...

---

### Post by adwait on 2005-10-14
You could download and burn the CD. Then edit your sources.list and remove all the repositories (or comment them out) and just add a cd rom repository. Then run apt-get update and apt-get dist-upgrade. It will just use all the files off the CD ROM instead of downloading them.

---

