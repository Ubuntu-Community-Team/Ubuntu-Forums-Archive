---
title: "Can ubuntu boot directly to software raid?"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by woutersamaey on 2011-08-08
A while ago I learned that Ubuntu, using Grub2 should be able to boot directly to a software raid volume. The idea is here that all disks are in a raid volume, and I dont need a non-raid disk anymore.

Is this now a working feature? And, can I install directly using the alternate installer, or are some extra steps required to get things working (i.e. install without raid then setup everything later :s)?

Or, do you still need a small separate disk (maybe like a USB drive) to boot?

My intention is to setup a home NAS, and use RAID 10.

Tnx in advance.

---

### Post by YesWeCan on 2011-08-08
In 11.04's Grub 1.99 booting RAID directly is supported.
Just use the alternate installer.
No need for a separate boot partition.

---

