---
title: "Filesystem with encryption, snapshots and caching on SSD"
date: 2014-02-28
forum: Installation &amp; Upgrades
---

### Post by Bromskloss on 2014-02-28
I'm about to install Ubuntu on a computer with one HDD and one SSD, and I would like to know if it's possible to achieve all three goals below simultaneously.

**0.** Encryption (should I use disk-level or filesystem-level?)
**1.** Snapshots (for making backup copies of with rdiff-backup; suggestions of better backup solutions are welcome)
**2.** Enjoy the speed of the SSD without manually choosing which files goes on which drive. I'm thinking of the following possibilities:
[indent]**2.0** Store everything on the HDD and have the OS use the SSD as a cache. (Perhaps reading from and writing to both drives simultaneously for speed.)[/indent]
[indent]**2.1** Use both the HDD and the SSD as a single, big drive, and have the OS shuffle things around so that the most used stuff resides on the SSD. (Again, perhaps reading from and writing to both drives simultaneously for speed.)[/indent]

What filesystem can do this for me?

---

