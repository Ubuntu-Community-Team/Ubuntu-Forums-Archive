---
title: "Disk ordering changed after install"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by dentharg on 2008-09-03
Hi!

I have 2 disks: new SATA drive connected to SATA :) and an old ATA drive connected to PATA JMicron but working in AHCI mode.

During Kubuntu installation the SATA was detected as /dev/sda, and pata as /dev/sdb.

Yet when I enter
```
mount
```

I get that my / partition is /dev/sdb2 and not /dev/sda2. Even the comment in /etc/fstab mentions that / is /dev/sda2!

Can someone please explain to me why did this happen. Nothing like this happened during my previous install of 8.04.

---

### Post by Terry19 on 2008-09-03
well u said it kinda confusing there. But i think linux will put sata first because its newer. I have a sata dvd rom and it never works proply because of linux ubuntu. so i might be havving simular problems. All in all is ur computer working as it should?

---

### Post by dentharg on 2008-09-03
That is the problem. During install /dev/sda is SATA. However after reset and start from disk it becomes /dev/sdb. Ubuntu starts properly because it uses UUIDs.

Yet this device swap is very confusing.

---

