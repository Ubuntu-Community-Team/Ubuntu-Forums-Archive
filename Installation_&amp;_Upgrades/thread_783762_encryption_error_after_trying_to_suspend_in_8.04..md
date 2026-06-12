---
title: "encryption error after trying to suspend in 8.04."
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by fuzzy_umbra on 2008-05-06
Hello,

I just upgraded from 7.10 to 8.04.  In 7.10, I had the hard drive partitions encrypted.  After upgrading to 8.04, I tried to "suspend" to see how things were coming along on that front.  The computer shut down and now every time I start up and enter my encryption pass phrase, this error appears:

"the check for '/dev/mapper/sda4_crypt' failed.  /dev/mapper/sda4_crypt contains data: - The device /dev/mapper/sda4_crypt contains a valid filesystem type suspend."

So it seems I have lost my swap partition to the suspend process.  I looked at my partition info. with GParted, and /dev/sda4 (which was /dev/mapper/sda4_crypt) shows a file system of "unknown".

I'll just back up and recreate an encrypted swap partition.  But, has anyone else hit this?  Do the Ubuntu folks know about it?  I saw a similar issue posted here, but there wasn't really a solution:

[http://ubuntuforums.org/showthread.php?t=676822&highlight=valid+filesystem+type+suspend](http://ubuntuforums.org/showthread.php?t=676822&highlight=valid+filesystem+type+suspend)

Thanks!

---

### Post by Zer0Nin3r on 2008-05-25
Been having the same [problem]("http://ubuntuforums.org/showthread.php?t=807394").

If I make any progress I'll post it up on my thread.

---

