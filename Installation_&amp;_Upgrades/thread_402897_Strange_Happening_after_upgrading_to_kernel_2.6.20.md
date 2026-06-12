---
title: "Strange Happening after upgrading to kernel 2.6.20-14 (Feisty)"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by Najand on 2007-04-06
I installed Fesity a few days ago to evaluate it on one of my computers in Univ. It was working fine and I was too busy to look what is new about it. Today I came to my computer and tried to figure out what is going on in Fesity, when I found there are a bunch of new updates so I just updated and upgraded my Ubuntu using apt. I saw one of the upgraded packages is the Kernel 2.6.20-14 so I rebooted my computer and I saw everything went wrong. Well... I have different partitions for /(root), /boot. /home and /usr and by reviewing the error messages I found out that the problem is that fsck cannot find any of them. I used the recovery mode and I found out that all partitions on the IDE harddisk are loaded with /dev/sda* devices. I checked fstab and found out that they used to be /dev/hda* devices. So I changed all of them in fstab to /dev/sda* and rebooted my computer. It works fine now, but I am very surprised why IDE HD partitions are shown as sda devices. Anyone else has the same experience? If so, let me know to file a bug for it in Launchpad.

---

### Post by frodon on 2007-04-06
This seems to be a bug, you can add your comment on the launchpad bug report. The more comments added the more devs attention you get.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314)

Or maybe fill a new if you think your bug is a bit different.

---

### Post by Najand on 2007-04-06
That was fast frodon. Thanks.

---

### Post by frodon on 2007-04-06
I was reading this bug report ;)

---

