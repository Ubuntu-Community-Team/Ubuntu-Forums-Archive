---
title: "Ubuntu dmraid ONLY show 1.6TB in 8TB mirror"
date: 2021-05-06
forum: Installation &amp; Upgrades
---

### Post by will1017 on 2021-05-06
We got some problem during we form a RAID1 (Mirror) of 8TB SATA x 2 for Data Disk in HP Z4 G4, after creation completed, we check that the volume only 1.6TB.

We want to know :

1. Can we extend the size of the volume ?
2. Is it Ubuntu NOT support the size more than 2TB?

Thank you very much!

---

### Post by TheFu on 2021-05-06
MSDOS partition tables only support 2TB.  To get beyond that, a GPT partition table is required.  That's my first guess. It might not be correct.

**sudo fdisk -l**  will output the partition information.  Please post using [COLOR="#FF0000"]_code-tags_[/COLOR] [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) for all the output and remove all the "loop" devices before posting.  Those have nothing to do with real storage and just add cruft/crap, which takes away from the important information.  Please don't make people wade through the swamp to see the important data.

BTW, I though dmraid was deprecated a few years ago. Shouldn't you be using **mdadm** to setup RAID now?

Which Ubuntu release?

---

