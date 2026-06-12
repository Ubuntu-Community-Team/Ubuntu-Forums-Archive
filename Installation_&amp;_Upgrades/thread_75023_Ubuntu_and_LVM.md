---
title: "Ubuntu and LVM"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by kashms on 2005-10-13
Hi,

I have split my harddisc into several partitions which I used to test different distributions. I have now settled on Ubuntu and will install Breezy. But I would like to use lvm to combine the partitions for Ubuntu.

Is it possible with the Breezy CD to install LVM (make logical volume) in one partition, install Breezy, and extend the space by adding more partition later on?

Any experiences?

---

### Post by Yoooder on 2007-02-22
Hmm...  Do you really need the seperate partitions?  It would be a lot easier to setup LVM if you combine those partitions into a single partition (or as few as possible).

I haven't tried installing Ubuntu into an LVM volume, but I wouldn't recommend it.  I use LVM to hold all of _my_ files, not Ubuntu's.  This way if LVM is ever broken I can at least get into the OS to work on it.  Otherwise you would have a lot more hurdles to recovering from an LVM problem.

I would say make your root partition small, and use LVM volumes for things like your /home and /var/ directories that hold files you use, but aren't necessarily required by the OS.

It all boils down to keeping things simple.

---

