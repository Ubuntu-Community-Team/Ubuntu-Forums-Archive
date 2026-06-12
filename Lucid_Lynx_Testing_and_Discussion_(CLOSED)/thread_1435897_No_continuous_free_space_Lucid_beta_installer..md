---
title: "No continuous free space Lucid beta installer."
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Madspyman on 2010-03-22
OK, after upgrading my alpha to the beta prematurely and having my panel, nautilus, and my network manager break, I decided to boot back up karmic and kill my Lucid partition in favor a fresh beta 1 install.

When I chose the option for "use the largest continual free space" and hit OK I got this error message "unable to satisfy constraints on the partition" followed by "can't have overlapping partitions" followed by "this probably happened because there are too many primary partitions in the partitions table"

I ended up just manually partitioning my unallocated space, and swap space.

This never happened in the alpha, is this just a bug or does Ubuntu not want to share space unless it's forced to? Thats no problem for me, but it's really not very new user friendly.

---

### Post by dino99 on 2010-03-22
This is not a bug, only a mess: there are too many primary partitions in the partitions table.

Learn how to organize your hdd: run gparted and see the mess, you might know some rules to format. Why not using an existing unsused partition ?

---

### Post by Madspyman on 2010-03-22
> **dino99 said:**
> This is not a bug, only a mess: there are too many primary partitions in the partitions table.

Learn how to organize your hdd: run gparted and see the mess, you might know some rules to format. Why not using an existing unsused partition ?

This option worked great in Jaunty, Karmic and the Lucid alpha. I had 2 primary partitions, the Lucid alpha and Karmic. I ran gparted to delete my alpha Lucid partition, leaving one primary partition/swap and unallocated space. Tried to install the beta using the same method I always use, the same way I always use it (not my first barbecue) and it didn't work.  

I always keep a stable partition and a test one, if something goes wrong with the test one I deleted in gparted and reinstall to the free unallocated space, it's fast, and it always works, until the Lucid beta.

Maybe I should try the alpha installer again just to see whats up.

---

### Post by dino99 on 2010-03-22
oh i see, sorry i did want to be rude :oops:

so, maybe a gparted problem. How have you formated the partition, try to use gparted with karmic or reformat again. If the table is wrong, run a fsck ( might find which param to add)

---

### Post by Madspyman on 2010-03-22
> **dino99 said:**
> oh i see, sorry i did want to be rude :oops:

so, maybe a gparted problem. How have you formated the partition, try to use gparted with karmic or reformat again. If the table is wrong, run a fsck ( might find which param to add)

There's really no formating involved until I install Ubuntu. I delete the partition completely using gparted, this leaves unpartitioned unallocated free disk space. The Ubuntu installer has an option to install to this space "use largest continuous free disk space", there's really not much science involved, it formats and adds the swap space, so I don't have to. It's a very efficient system.

I'm gonna try it again later with the Lucid Alpha 3 disk, and see what happens, then I'll try it again with the Beta, maybe I'll document it on video this time.

---

### Post by NCLI on 2010-03-22
Try a reformat and an install on another PC with the same setup, if you can. If it doesn't work, please report it as a bug.

---

