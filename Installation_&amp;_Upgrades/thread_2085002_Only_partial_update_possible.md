---
title: "Only partial update possible"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2012-11-17
I am using 12.04 ubuntu on an asus and, since I installed it, whenever the update manager asks me to update/upgrade it also states that only a partial update/upgrade is possible

I've gone to the settings and ticked every possible box so that it will take updates from all possible servers and sources but it keeps on showing that only partial update is possible....

anyone who had the same issue?

---

### Post by xskydevilx on 2012-11-17
Have you tried opening up the Terminal and running
*sudo apt-get update*
and then possibly either
*sudo apt-get upgrade* or *sudo apt-get dist-upgrade*?

---

