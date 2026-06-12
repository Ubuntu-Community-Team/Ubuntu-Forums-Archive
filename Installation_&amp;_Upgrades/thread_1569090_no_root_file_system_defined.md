---
title: "no root file system defined"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by sabneus on 2010-09-06
[FONT=Arial][SIZE=2]Dear friends,

I am windows user and I want to try the Ubuntu 10.04 LTS edition.

In windows I created a partition for Ubuntu (with NTFS File System).

Now I have a CD of Ubuntu so I restart the system with inserting the CD.

Now when i specify the drive where i want to install ubuntu it says 

"[/SIZE][/FONT][FONT=Arial][B][SIZE=2]no root file system defined"

Please help.
:-s
[/SIZE]
[/B][/FONT]

---

### Post by Rubi1200 on 2010-09-06
Ubuntu and Windows file systems don't really play nicely together (well, they can, but that's another story).

Boot the computer with the Ubuntu CD and use GParted to prepare the partition you want by leaving it unallocated (no filesystem). Don't choose a file system for the partition.

Then, run the Ubuntu installer and choose the option to install to the largest continuous free space.

---

### Post by sabneus on 2010-09-06
Dear Rubi,

Is the Gparted is inbuilt in CD?

Sorry for the inconvenience.

Regards

---

### Post by Rubi1200 on 2010-09-06
> **sabneus said:**
> Dear Rubi,

Is the Gparted is inbuilt in CD?

Sorry for the inconvenience.

Regards
Yes it is and there is no inconvenience; ask as many questions as you want :)
(I actually thought after I posted that I should have said that :-()

---

### Post by BbUiDgZ on 2010-09-06
> **Rubi1200 said:**
> Yes it is and there is no inconvenience; ask as many questions as you want :)
(I actually thought after I posted that I should have said that :-()
[look at screenshot here](http://grow-room.org/purplehaze/4knacky.jpg) 

I took this screenshot for a friend some time ago who asked the same question :D

---

