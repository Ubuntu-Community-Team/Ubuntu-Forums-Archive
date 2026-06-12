---
title: "Ubuntu 12.04 install"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by hockey9876 on 2012-05-14
I recently installed ubuntu 12.04 on a laptop, upgrading it
from v10.x.  One of the changes in the grub.cfg file over
the old menu.lst file is that where it used to say (hd0,0).
Now it says root='(hd0,msdos1)'

What is this msdos1 entry, and why did it change?  I've tried
google, but didn't see anything that caught my eye.

Thanks,

John

---

### Post by Quackers on 2012-05-14
The old grub (legacy) used to count partitions from 0. The new grub(2) counts partitions from 1.
So (hd0,0) in the old system was the first partition on the first drive.
In the new grub (hd0,msdos1) is the first partition on the first drive.
The msdos part refers to the formatting type of the drive - in your case MBR, as opposed to GPT.

---

