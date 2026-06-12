---
title: "how to make a new partition outside current extended partition?"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by regkonto on 2012-04-22
I want/need to make a new partition for Win7 (just for testing ;)). The problem is that W7 needs 2 partitions, one can only make 4 for a single drive and I already have 3 on mine for Kubuntu. I have free space for the new partition, but in Partition manager it's under an extended partition (see the pic). And I can't figure out how can I make the new partition to be outside of that extended partition.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216437&stc=1&d=1335121682[/IMG]

---

### Post by darkod on 2012-04-22
1. Win7 will install itself on two partitions only if you use the win7 installer to create the partition for it. If there is a ntfs partition existing, it will install on it, using a single partition. So, if you create one ntfs partition outside the extended, it will use it.

2. To make the unallocated space "go out" of the extended partition, you will need to boot into live mode first, unmount swap which gets mounted automatically in live mode, and shrink /dev/sda2 so that the 90GB are not included in it any more. After that you can create a primary ntfs partition from them.

---

### Post by regkonto on 2012-04-23
Thanks for the help. Worked like a charm.

---

