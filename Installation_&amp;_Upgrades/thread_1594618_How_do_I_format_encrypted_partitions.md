---
title: "How do I format encrypted partitions"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by dhavalbbhatt on 2010-10-12
So I messed up. I downloaded 10.10 64bit alternate version yesterday and started to install the system today. I was running 9.10 on one of my hard drives (I have another HDD that has Windows on it) and wanted to install 10.10 on that one. Since the 9.10 was a ext3 and I wanted an "encrypted" ext4, I somehow managed to encrypt the HDD (using the installer), but now, when I try and install the system, it says to provide a /boot outside the encrypted filesystem, otherwise it won't be able to access init files. At this point, not understanding any of the above, I would just like to format the HDD to just regular ext4 - can that be done? If so, how? (BTW, I tried using the partitioner to format, but the partitoner won't allow any changes to the encrypted filesystem).

Looking forward to replies.

Thanks all for your help.

Dhaval

---

### Post by dhavalbbhatt on 2010-10-12
I got this resolved - I had to re-boot during installation and then select guided partition to format the HDD. 

Thanks,
Dhaval

---

