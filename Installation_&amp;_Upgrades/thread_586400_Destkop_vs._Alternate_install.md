---
title: "Destkop vs. Alternate install"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by hyper_ch on 2007-10-22
I've been wondering for a long time why the alternate install take a lot longer to install than the desktop one (I mean from the poing after creating the partition and setting up to user - where the installation of files actually starts).

Any explanation?

---

### Post by bergersau on 2007-10-22
The Live CD essentially copies a system image onto your hard drive.  A little like Norton Ghost for Windows you could say.
The alternate install extracts and installs packages individually -  I think dpkg is the mechanism used but I'm guessing.

That's a simplistic explanation but I think it's broadly accurate.

The advantage of the alternate install is it gives more control for non standard partitioning, raid, server installs with no x server etc.

The live CD is good for getting my windows running friends out trouble when their PC won't boot and I need to recover their data before a clean install.

I keep a copy of both the Live and Alternate CD on hand.

---

