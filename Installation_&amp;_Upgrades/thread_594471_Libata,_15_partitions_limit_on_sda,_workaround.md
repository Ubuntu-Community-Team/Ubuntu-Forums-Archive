---
title: "Libata, 15 partitions limit on sda, workaround?"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by plamen_todoroff on 2007-10-28
First of all, I'm a Linux newbie and I can say Linux is the best thing happened to my computer since the day I bought it, I've tried a lot of distros and I liked a  few I decided to keep, so... I'm a multi-distro user and i've partitioned my single PATA HDD in 20 partitions, and apparently there is a problem for Gutsy to handle all of them because of the new way PATA HDD-s are managed by the new libata drivers, which treat hda as sda, thus limiting the number of allowed partitions to 15 (due to the scsi standards). And here is my question: is there some boot parameter that i could enter at the install prompt in Gutsy which will make the install process use the old PATA drivers from Feisty? I have to install Gutsy in the hda17 (/) and hda18 (home) partitions but the installer doesn't access them at all. In Feisty all my 20 partitions were handled quite nicely.
Here is a link to a thread I posted couple of weeks ago and it's about my Feisty HDD expirience: [http://ubuntuforums.org/showthread.php?t=565986](http://ubuntuforums.org/showthread.php?t=565986)
I'll appreciate any answer to this or to the other thread as they are quite linked. Thank you.

---

### Post by plamen_todoroff on 2007-10-28
Aren't there any multi-distro users with the same problem, I think this is a major issue, am I the only one with this problem?

---

