---
title: "Ubuntu won't shrink NTFS partition"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by takisan on 2010-06-16
Having using full-time on Windows (as a "trip down memory lane") I decided that Ubuntu is way better. Now, it won't resize my full-drive NTFS partition. I can move it on the drive, but I can not resize it.

HELP PLEASE!

---

### Post by darkod on 2010-06-16
This is not nearly enough info. Can you post a screenshot of Gparted please?

How are you trying to resize it? Is there a triangle warning mark next to the partition in Gparted?

---

### Post by takisan on 2010-06-16
Yes. there was an exclamatory triangle next to the partition in GPARTED. I shut down and am using DamnSmall for the moment.

---

### Post by darkod on 2010-06-16
The triangle means there is some sort of error on the partition, which might not be a serious error at all. But as long as it's there, Gparted will not touch it for resizing.

You can try to boot windows and run chkdsk from it. The command is:

chkdsk c: /r /f

After that check in Gparted if the triangle is gone.

---

