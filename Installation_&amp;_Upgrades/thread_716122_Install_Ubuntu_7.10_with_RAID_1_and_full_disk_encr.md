---
title: "Install Ubuntu 7.10 with RAID 1 and full disk encryption"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Moso on 2008-03-05
Hi everbody! :)

I want to install Ubuntu 7.10 with RAID 1 and full disk encryption.  I have searched the forum and Google and none of the tips I have found made it work.

I am using the alternate CD to do a text install.

The option "Guided - use entire disk and set up encrypted LVM" works great but without RAID 1.

Using manual partition I can do RAID 1 work but without disk encryption.

My HDs have 40GB.  I want to create a 500 MB partition to use with "/boot", a 1.7 GB partition for swap and the rest (37.8 GB) use for "/".

First I created the three partitions on the two HDs with "use as physical volume for RAID".  Then I configured the RAID.  Then I use two RAID devices (md1 and md2) to set up encrypted volumes.

When all is done I get the error: "The attempt to mount a file system with the type swap in Encrypted volume (md1_crypt) at none failed."

Someone can help me with a guide not too hard to follow to get this done on install of a new Ubuntu 7.10?

Sorry for my poor english and thanks in advance from a guy in south of Brazil.  :lolflag:

---

### Post by Moso on 2008-04-23
Exact same problem in Ubuntu 8.04 RC.

:P

---

### Post by analoog on 2008-04-24
[http://ubuntuforums.org/showthread.php?t=669282](http://ubuntuforums.org/showthread.php?t=669282)

^ maybe this topic can help you?

---

### Post by Moso on 2008-04-24
Thanks for reply but not the same problem...

I'm trying a workaround that involves to not set the swap partition and at the end of the install process to not reboot and do some more magic.

But what I really like is see this bug solved in 8.04 and not the same problem in the installer as in 7.10.

When I get it working I will try to make a "recipe" and put here.

:popcorn:

---

