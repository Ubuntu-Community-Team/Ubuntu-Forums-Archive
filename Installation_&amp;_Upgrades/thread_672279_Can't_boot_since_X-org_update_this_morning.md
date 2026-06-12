---
title: "Can't boot since X-org update this morning"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by DaveRowell on 2008-01-19
When I try to start Ubuntu 7.04 after this morning's x-org update nothing happens except "GRUB __" shows in the corner of the screen - it doesn't even get as far as choosing what to boot.

Ubuntu 7.04, no 3D effects, S3 Unichrome onboard graphics, Via KM400A chipset
I'm dual booting using XP's boot loader with Grub on the / partition.  This scheme has been successful for a year or so untill this update.

Writing this from a Xubuntu live CD.  All My partitions mount, my data is there.

What can I do to recover???
===============================================
Turns out that the "upgrade" caused the first sector of the / partition to be rewritten.  Windoze XP actually executes a copy of that sector when it boots Ubuntu.  So therefore Grub becomes confused and goes off to sulk!

I finally found my notes from the last time x had a major "upgrade" (almost exactly a year ago!) that created the same problem.  I'll try to save my notes better this time!

---

