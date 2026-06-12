---
title: "[SOLVED] [Errno 5] Input/output error"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by hmotwell on 2008-08-22
trying to install 8.04.1 from live cd.
i get following error while its copying files:
 [Errno 5] Input/output error
output from cat /proc/partitions:
 8     0   19531250 sda
   8     1   18675531 sda1
   8     5     851413 sda5
   7     0     685352 loop0
ubuntu@ubuntu:~$

---

### Post by Partyboi2 on 2008-08-22
If you downloaded the ubuntu live cd iso did you check that the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") matched? Another thing to do is to check the cd for defects (option 5 I think) If they all pass then you could try installing with the [[COLOR=Blue]alternate cd [/COLOR]]("http://releases.ubuntu.com/8.04.1/")which has worked for some who have had this problem.

---

