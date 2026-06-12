---
title: "How to re-mount /home directory to a new partition"
date: 2017-12-05
forum: Installation &amp; Upgrades
---

### Post by nimble2005 on 2017-12-05
My current OS is Ubuntu 14.04 and I have to reinstall the OS due to my incorrect installation of CUDA Toolkit. 
The problem is that I directly mounted the '/' directory to the entire hard drive in the initial installation and many data in '/home ' directory are now very important. So is there a way to re-mount the '/home' diretory to a new parition on the current hard drive in order to maintain these data when reinstalling the new OS? THX.

---

### Post by Impavidus on 2017-12-05
If I get it right you want to move your /home directory to a separate partition. That indeed makes reinstalling easier and it isn't very hard, provided you have enough free disk space to rsync all data directly from the root partition to the /home partition. See this guide: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

It shouldn't be too hard to follow. I managed it on my first attempt years ago, much less experienced than now.

---

