---
title: "Problem with startup after installation"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by ashishgoel on 2007-05-15
i'm facing number of problem while installing n runnin Wubi but even then not able to get thru...

1. I've got 8 partitions of my 80 GB - of which one is primary n rest are logical. I tried Installin Wubi on 4.65 GB empty partition- i selected .1 GB as Home n virtual disk size as 1 GB needs to be free. After copying and restart - After "boot" comes up, it says NO RAID Disks - and no further installation happened.

2. Then i tried installing it on my main root partition with 5.65 GB space free, with defaults options choosen. It also gave NO RAID DISKs but installation continued. Wubi - Ubuntu installed in half an hour - smooth - no prblem at all, but when it restarted after it, the startup of UBUNTU stopped at 10% (the loading bar stopped movin) and no further activity.

Couldn't find solution to that. 

Please help

---

### Post by jerrylamos on 2007-05-15
Well usually you'd install Ubuntu on a blank partition.  Wubi is for installing inside a running XP system effectively as a file inside XP's partition, as I understand.

Have you tried installing Ubuntu in an empty partition?  Note you will need a swap partition also, about 512 mb to 1024 mb.

Cheers, Jerry

---

