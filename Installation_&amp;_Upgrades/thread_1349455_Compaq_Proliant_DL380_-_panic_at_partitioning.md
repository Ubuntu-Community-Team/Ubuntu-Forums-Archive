---
title: "Compaq Proliant DL380 - panic at partitioning"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by ccf on 2009-12-08
Inherited one of these recently.  No suffix on the box, so I'm guessing it's from the original line.

After removing one of the disks from the array (it had failed), going through the whole Smart Start nonsense, and discovering the built-in CD drive was pants, I finally got to the partitioner, set up three partitions on the array (/boot, swap and / - 100MB, 2GB and 34GB respectively).  When it came to format / as ext4, I got a panic.  Couldn't make out the error message on vt4 because the stack dump pushes it off the screen before I even notice it's there.  I'm assuming I can just partition and install straight onto the array rather than having to use LVM, given the RAID etc. is already done in hardware.  The kernel is 2.6.31, so blacklisting the sym53c8xx driver doesn't have any effect.

I'm also being prompted to hit F1 at boot (this apparently doesn't time out), though this is probably something completely different.

Any thoughts?

---

