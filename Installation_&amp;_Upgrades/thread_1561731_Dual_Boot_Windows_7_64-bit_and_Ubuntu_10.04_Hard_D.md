---
title: "Dual Boot Windows 7 64-bit and Ubuntu 10.04 Hard Drive Issues"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by chaosfactor on 2010-08-26
I have a laptop I want to dual boot Windows 7 64-but and Ubuntu 10.01 on, but when I go through the install on the live CD for the partitioning section it shows the disk as 100% free instead of the 300GB NFTS partition and the 200GB of free space of the linux install.

I though it was and issue with Ubuntu but I tried it on Fedora 13 and I get the same thing.

Has anyone successfully install Ubuntu 10.04 next to 64-bit Windows 7?

---

### Post by oldfred on 2010-08-26
Welcome to the forum.

Have you used all 4 primary partitions? Then the auto installer cannot use the free space as you cannot create any more partitions. Many win7 systems have this issue as win7 has added a boot/recovery partition and the vendors then add two more, system recovery partition and a utilities partition.

From liveCD post this:

```
sudo fdisk -lu
```

---

### Post by srs5694 on 2010-08-26
Check my Web page on this issue: [http://nessus.rodsbooks.com/missing-parts/index.html](http://nessus.rodsbooks.com/missing-parts/index.html)

---

