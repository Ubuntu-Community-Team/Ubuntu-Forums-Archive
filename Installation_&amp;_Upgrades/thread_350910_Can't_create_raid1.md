---
title: "Can't create raid1"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by mokum on 2007-02-01
Hi,

While trying to install edgy with raid1, I made a mistake. The first time I got a menu-item 'Configure raid', but not any more. I can choose 'Use as : Raid physical' but then I'm not able to designate a mount point. I remember a message the first time, stating that something was irreversible.

So now I have 2 disks with each a swap partition hd[ac]1 and a root partition hd[ac]2. I tried to create a raid array with mdadm:
  mdadm -C -l1 -n2 /dev/md2 /dev/hda2 /dev/hdc2  but it says:
  mdadm: error opening /dev/md2: No such file or directory

Could somebody give me hints as to how to create the arrays and how to be able to boot with them?

Would it be possible to rewrite the partition table so that I could have the menu option of configuring raid again?

---

### Post by Spyder_23456 on 2007-02-01
Could someone explain to me how to get Ubuntu to run on an HP Pavilion? It keeps freezing up everytime I try to install Ubuntu 6.06.

---

