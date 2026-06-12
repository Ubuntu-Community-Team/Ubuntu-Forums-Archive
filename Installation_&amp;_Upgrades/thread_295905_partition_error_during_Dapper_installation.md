---
title: "partition error during Dapper installation"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by robli99 on 2006-11-08
Never passing checksum test after burning 6 Edge CDs, I have to give up Edge and turn to Dapper. I burn Dapper iso to CD at high speed, X48. It startup successfully at the first time. But when I try to make partitions for new installation, error occured. I have a 80GB Maxtor Sata HD, WinXP installed on C:(ntfs, 20GB), D: (fat32, 20GB). FC6 is installed in the rest 40GB (/boot,/swap, and /). I tried to use the exist partition, but I am told the filesystem is unrecongnized. So, I deleted the 3 linux partition, and tried to creat 3 new. I successfully created 100MB for ext3, 1GB for linux-swap, but I failed to use the rest 38GB for another ext3 partition. I was just told error occured during generating the partition. 
I can still start up WinXp on this HD, but can't start up FC6 because the partitions have been deleted.

Is there any size limition of partitions for Dapper on sata HD?

---

### Post by ThrobbingBrain66 on 2006-11-08
when making the new partitions, were you using gparted or were you trying to do this after starting the install process?

---

### Post by robli99 on 2006-11-08
I just use the partition option inside Dapper after starting the install process.

---

### Post by ThrobbingBrain66 on 2006-11-08
if i remember correctly, in dapper that was always a little buggy for me.  i would try to use gparted in system>admin>gparted, you may have better success with this

---

### Post by robli99 on 2006-11-08
Thanks  ThrobbingBrain66.
I didn't explore the system tools. This is the first time for me to touch Ubuntu linux. I just clicked "Install" immediately after the system was up. Actually the whole system has started up so I can use the system tools inside instead of the installation tools. This is really an advantage of Ubuntu.

---

### Post by robli99 on 2006-11-09
Can any one give some instruction to do MD5SUM check in WinXP system?

---

### Post by ThrobbingBrain66 on 2006-11-09
this should help you out.

[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

---

