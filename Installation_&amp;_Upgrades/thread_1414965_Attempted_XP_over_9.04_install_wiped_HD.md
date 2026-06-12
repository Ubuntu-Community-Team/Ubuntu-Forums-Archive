---
title: "Attempted XP over 9.04 install wiped HD"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by cchhrriiss121212 on 2010-02-24
I gave my old laptop with ubuntu 9.04 on it to a friend which they liked, but they also wanted XP on it for work. I said I could install it for them. I know it is easier to install windows first, but I had done it the other way successfully on the same laptop before.

First I resized the home partition to make 20GB room for xp in gparted on a live cd. The xp install screen regognised my existing partitions but said it could not install as it had an incompatable partition. It reccommended I delete existing partitions to make room which is not what happened the last time. I quit the install and rebooted whcih gave me an "error loading operating system" message. Loaded up gparted via a live cd and I now have 55GB space unallocated which is the entire hard disk.

So did I do something wrong here, or is this normal windows behaviour?

---

### Post by dstew on 2010-02-24
I don't know much about XP installation, but I think it wants to be in a primary partition. If you had all 4 primary partitions already used, and tried to put it into a logical partition, I am pretty sure it would not be happy about that. Whether it quits nicely or damages the partition table, like it seems to have done, I don't know, you might have to ask Windows people about that.

By the way, you can probably reconstruct your partition table. The Testdisk program is the best. See [this Ubuntu document]("https://help.ubuntu.com/community/DataRecovery").

---

