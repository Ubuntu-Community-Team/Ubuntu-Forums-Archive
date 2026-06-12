---
title: "Ubuntu 10.04 and ubuntu 10.10 in the same laptop"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by marticc on 2010-10-23
Hi. I have Ubuntu 10.04 installed in my laptop in a partition and I am quite happy with it as it works great. In my laptop I also have another partition with windows 7.

The problem is I would like to try Ubuntu 10.10 without deleting neither W7 nor ubuntu 10.04 (I would like to check that everything works alright before upgrading Ubuntu 10.04).

My plan is to install Ubuntu 10.10 in windows 7 using wubi (I have used Wubi wuth ubuntu 8.10 and 9.04 and i did not have any problems with it).

Do you think that I will have any problems starting my laprop having Ubuntu 10.04 in a partition and Ubuntu 10.10 with W7 in other parition?, I am afraid of having any problems with GRUB.

Thanks for your asnwers and sorry for my poor English.

---

### Post by ajgreeny on 2010-10-23
No reason why it should give you any problems, but why not just make a new small partition of about 10GB and install into that.  You can then mount your current 10.04 partition at boot time with a simple edit of /etc/fstab in the new 10.10, and create links to all your data folders in that to the new 10.10 partition's home folder.  That way you can work on all your data files from either OS without a problem.

Come back again if you want more info on how to do it.

---

