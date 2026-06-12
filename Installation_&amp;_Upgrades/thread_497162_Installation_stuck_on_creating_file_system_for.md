---
title: "Installation stuck on creating file system for /"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by cmillican on 2007-07-09
I'm installing Ubuntu 6.06 on an older Toshiba Satellite, and the bar hasn't gone very fast, and it's been stuck on "Creating ext3 file system for / in partition #1 of IDE1 master (hda)..."...did I do something wrong? It did this in Kubuntu and froze the screen, so I put in Ubuntu and it's been 10 minutes and it's at 1%...any help is appreciated.

Thanks,
Chris

---

### Post by Odrodzona-Sarmacja on 2007-07-10
Try pre-formating the ext3 partition for ext3 with other tool then ubuntu installer.

Unless the partition you try to pre-format is already ext3, then you need first to destroy it by changing it to fat32 and low formating it. Somehow ubuntu installer does not format ext3, but scavenges it even if it is a corrupted ext3 partition.

In ubuntu installer then just choose manual setup and mark the pre-formated ext3 partitions as "/", "/home/","swap" and so on.

---

