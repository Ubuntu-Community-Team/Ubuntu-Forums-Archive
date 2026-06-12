---
title: "Can't create startup disk on external 2.5 inch sata?"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by Squerl101 on 2012-03-04
Hey guys, i just bought a sata enclosure, and i hook it up and it mounts ok and I can read/write, but when I want to create a startup disk, the disk doesnt show up there. I have a feeling that the partition might have to be formatted a certain way for that to happen. Any help GREATLY appriciated.

---

### Post by darkod on 2012-03-04
All disks and partitions show up if you run:
sudo fdisk -l (small L)

See if that shows your disk in the enclosure. If it does, making partitions on it is no problem, the main issue is whether it shows or not.

---

