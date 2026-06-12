---
title: "Edgy partitioning problem over dapper installation"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by sarikan on 2006-12-21
Hi there, 
I have decided to go for a fresh installation of edgy to my laptop, which at the moment has drapper. Drapper is installed on /dev/sda3 (mounted /) and has /dev/sda6 as swap.
When I run the installer, it gives me an empty hd on the partitioning screen (normally, should not I see my existing partitions, drapper and xp?). 
Since I do not want to delete my xp installation and I am fine with the partitions I do nothing and click forward, and I get screen where edgy correctly offers to mount root as it is and swap as it is; I leave reformat options checked and click forward, but I get a warning saying there is no root partition, and I should fix it from the partition menu????
The installer correctly recognizes the current root and swap, but somehow it does not go on. There is nothing I can do on the partitioning screen, since all I get is a blank disk, which needs new partitions according to installer. If I create a new part. all I have is gone. 

Does this problem sound familiar? What am I doing wrong?

Best Regards
Seref Arikan

---

### Post by derby007 on 2006-12-21
I've seen the same issue: 
see my thread at : [http://ubuntuforums.org/showthread.php?t=322827](http://ubuntuforums.org/showthread.php?t=322827)
Can anyone help us here ??

---

### Post by Benchrest on 2006-12-21
I just installed Edgy on my laptop last night on the same partitions I had Hoary installed. I assume your selecting the 3rd option to manually edit your partitions. On mine, When the partitions came up they were all there except the root partition didn't show as a root. I had to manually change it to root. I had heard this was normal somewhere else on this forum.

---

### Post by derby007 on 2006-12-21
Do u mean u got rid of Hoary & upgraded to Edgy, as i was trying to get 2 Ubuntu's going on 2 diff partitions, but it gave me problems....as i have/had Dapper.

---

### Post by sarikan on 2006-12-21
Hi there, 
Well, problem solved; actually I have been adding and removing this partition again and again using imaging software, and somehow ubuntu did not like the way the partitions are setup. 
So I removed both the / and swap partitions of dapper, and edgy did not cause any problems this time.

---

