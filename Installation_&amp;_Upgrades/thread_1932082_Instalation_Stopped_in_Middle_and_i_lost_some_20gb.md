---
title: "Instalation Stopped in Middle and i lost some 20gb in Harddrive"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by arunpar on 2012-02-26
Hi,

When i am installing Ubuntu in windows 7 it was stopped mistakenly i pressed CD it opened. Then i re-installed windows 7 in that partitioned window i cant able to see some 20gb in harddrive. I cant see tht 20gb size in my 320gb HD. Now i installed windows 7 in tht i installed Ubuntu also. How can i recover rest of the size?

---

### Post by Mark Phelps on 2012-02-28
You probably "can't see" the 20GB space because Windows does not understand Linux filesystems.

If you have Ubuntu installed and working now, boot into it, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on your drive and let us see what is there.

---

### Post by arunpar on 2012-03-05
see the attachment and u can able to see any missing space in the drive? What i segregate and partisioned in the drive is there exactely. And i installed ubuntu 11.04 directly installed in the drive and i upgraded to 11.10. This was the current status.. Thks for ur kind reply and response.

---

### Post by oldfred on 2012-03-05
You have 3 NTFS partitions, the extended partition and the three Linux partitions. Swap will not be shown in Linux and as posted before Windows does not see the Linux partitions. 

All the sectors are shown used from 2048 to the end of the drive which is normal.

What is the issue?

---

