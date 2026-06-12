---
title: "can I change size of root and  /home partition"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by blackadscft on 2007-09-08
i am using reiserfs format. I have root partition 6.5G, and /home partition 5G. I am trying to resize root partition to 8G, and /home to 3.5G without delete any partition. Actually I felt scary of doing that. Is there any tool like pq magic in windows system, which can finish this job.

I tried qtparted, i can only format or delete. also for gparted, I can only unmount them.

I would appreciate your suggestion. 

by the way, how can I use apt to install new package in /home dir? In this way, I can save space for root partition. thanks :):):)

---

### Post by zvacet on 2007-09-08
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by forestpixie on 2007-09-08
> by the way, how can I use apt to install new package in /home dir? In this way, I can save space for root partition. thanks

I don't know if you can accomplish this but you can clean the downloaded files out

```
sudo apt-get clean
```

---

