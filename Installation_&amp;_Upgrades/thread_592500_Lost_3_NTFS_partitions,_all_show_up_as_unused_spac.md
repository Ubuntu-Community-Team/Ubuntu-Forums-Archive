---
title: "Lost 3 NTFS partitions, all show up as unused space"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by chameleon_789 on 2007-10-26
Sorry, posted this in the general help forum but it's moving so fast no-one will see it.

Basically, I had 3 NTFS and a linux ext3/swap partition on my hard drive. Vista stopped booting and ubuntu stopped detecting my NTFS partitions, so I stuck in a copy of Hiren's boot cd which I had lying around and ran Partition Magic, which informed me that the boundaries of the partitions were incorrect, and that it could automatically fix them... except they weren't, and I let it fix them, and now all of the NTFS partitions are listed as unused space in all the partition tools I try, including the two partitions that were adjacent to each other, and the one after the Linux partition.

I've tried to repair the table using other tools on Hirens boot CD, but none of them detect the NTFS partitions. I also tried testdisk, which only detects the ext3 and swap partitions, and then hangs at 88% (I'm guessing this is the end of swap/start of the third ntfs partition). I also tried using a Vista install disk to repair but it hangs before I'm able to get to the automated recovery menu.

Usually by this point I'd give up and reformat, but I've got a lot of work I really can't afford to lose which is scattered around all three of the partitions. Is there another way of recovering the partition table, or am I relegated to data recovery software (if so, can anyone recommend some)?

---

### Post by spamking2000 on 2007-10-26
I had a similar problem recently after Clonezilla zapped all the partitions on one of my drives and then exited with an error. I tried several apps and even tried mapping the partitions back using fdisk based on their size, but I didn't have the sectors mapped out, so it was kind of guess work at that point.

Needless to say... nothing worked, that is until I tried testdisk. Testdisk was able to find and restore all of my partitions - however none of them were NTFS.

I would still recommend trying it again, maybe with a different live CD or just an ISOLINUX boot CD. If that doesn't work, and Partition Magic doesn't work... you may be stuck.

Partition Doctor is another software out there, but I haven't used it, so I couldn't tell you if it might work where Partition Magic has failed. Might be worth a try, but you also might spend $50 on software that won't help you.

Good luck!!

---

