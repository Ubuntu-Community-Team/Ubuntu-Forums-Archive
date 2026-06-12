---
title: "Recovering messed up partition table in RAID 0"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by sbubin on 2012-08-01
I would appreciate if anyone could give me a piece of advice regarding my problem. I have a desktop with three disk drives. The first one (an SSD) is a system disk, while the other two are HDDs and form a RAID 0 (FakeRAID, no separate hardware controller). I was installing Kubuntu 12.04 (to upgrade from Ubuntu 11.04) and messed up my partitioning badly. I did it a couple of times, I also made changes with fdisk. At the same time, I am sure I did not reformat the HDDs and no data was written on them (except for changing the partition). How can I recover the partition table on the HDDs? I really want to keep the data stored on the RAID. So my question is what is the procedure here? Are there any particular tools that can be of help. I googled something about testdisk. Is that the right tool?

Oh, and I forgot to say that the SSD was reformatted (I now have a working Kubuntu on it) so there is no information about the RAID array there (i.e. there is no old /etc/fstab or something like this). Unfortunately I do not remember how the RAID was originally managed (mdadm or lvm).

---

### Post by mowgliee on 2012-10-18
did you ever figure out/find a good solution?  b/c i have the same situation now!

---

### Post by darkod on 2012-10-18
Instead of posting in an old thread that has no answers, you should have opened a new one.
What exactly is your situation, because the original post is also a bit confusing at the end where the OP mentioned mdadm and lvm but at the beginning says he's using fakeraid.

mdadm is software raid, not fakeraid. And lvm is a whole different thing, not related to raid.

Did you mess up your partition table too? Is the raid array still together or not?

If the array is still together, testdisk might be the best option to recover the partitions, but I don't know if it supports fakeraid.

---

### Post by mowgliee on 2012-10-18
sorry about that. i posted new thread w/ all the details here:

[http://ubuntuforums.org/showthread.php?p=12302511#post12302511](http://ubuntuforums.org/showthread.php?p=12302511#post12302511)

but to answer you, i dont have sw or fake raid, only hw raid.  raid array is still together, preserved order etc, but cant boot or mount it or any individual disk from array.  i didnt mess up partitions (initially) but something did fail (drive, drives, raid card?).

thanx.

---

