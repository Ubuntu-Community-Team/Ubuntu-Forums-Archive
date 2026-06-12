---
title: "resizing partition"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by imsorrisuck on 2008-05-25
I have xp installed on 50 gigs and ubuntu installed on 50gigs. I wanted to have ubuntu around 10-20 gigs and more on xp part of HD. How can I do this?

---

### Post by Pumalite on 2008-05-25
Post a screenshot of Gparted

---

### Post by iaculallad on 2008-05-25
> **imsorrisuck said:**
> I have xp installed on 50 gigs and ubuntu installed on 50gigs. I wanted to have ubuntu around 10-20 gigs and more on xp part of HD. How can I do this?

You can use GParted to adjust your partitions. But you cannot resize partitions moving from right to left. It could not be possible if your NTFS filesystem is on the left and ext3 filesystem on the right.
But if you have the opposite, be sure to BACKUP all your important data/files.

---

