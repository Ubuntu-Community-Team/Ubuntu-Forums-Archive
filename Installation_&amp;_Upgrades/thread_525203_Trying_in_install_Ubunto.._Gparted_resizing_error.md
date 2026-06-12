---
title: "Trying in install Ubunto.. Gparted resizing error"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by minulescu on 2007-08-14
[B]ntfsresize v1.13.1 (libntfs 9:0:0)
ERROR: Device '/dev/sda1' is mounted read-write. You must 'umount' it first.[/B]

I do unmount the device, and try again, and I keep getting the same error.

I've been having huge trouble resizing/shrinking this partition.

I have just a C drive, with vista on it, and I want to shrink it so that I can put Ubuntu on it.

I have tried using Vista's partitioning software... that didn't let me shrink it. Then I tried partition Magic... that didn't do it either... I though G parted would for sure be able to.

What could possibly be the problem.

More specifically: From a live CD, Im using Gparted to try to shrink/resize my C drive (that is running Vista), and I get the error above.

Can anyone help? Thanks a lot.. It's been a struggle so far.

---

### Post by bwtranch on 2007-08-14
Have you tried just letting Ubuntu do it?

---

### Post by minulescu on 2007-08-14
Are you suggesting I try to just install Ubuntu on drive C? along with Vista?

I was under the impression that I should do it on a different parition.

Currently, if I run the Ubuntu installation there is no "free space" where I could install ubuntu, there's just drive C.

So I'm not quite sure what you mean by.. having Ubuntu do it.

---

### Post by merlinus on 2007-08-14
You have to use vista's disk manager to shrink its partition.

Delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after partitioning), and defrag several times.

Then try to shrink the partition, and afterwards you can install ubuntu.

-merlin

---

### Post by minulescu on 2007-08-14
Can you tell me what virtual paging is, and how to set it to 0?

Thanks!

---

### Post by merlinus on 2007-08-14
I never used vista, so try the help feature.  It is probably somewhere under System Tools/Advanced.

-merlin

---

