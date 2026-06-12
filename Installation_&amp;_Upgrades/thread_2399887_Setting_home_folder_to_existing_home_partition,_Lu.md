---
title: "Setting home folder to existing home partition, Lubuntu 18.04"
date: 2018-08-30
forum: Installation &amp; Upgrades
---

### Post by bs892 on 2018-08-30
Hello all. A 16.04 LTS install went awry, so I installed 18.04 on my first HD partition. It's an 8 GB partition set as the / directory. I want to set my second partition, a 230 gig partition which was my /home directory, as the /home directory. How do I do this? I used the alternate install image to install Lubuntu 18.04; I didn't see an option to set the second partition as home.

---

### Post by oldfred on 2018-08-30
Have not used Lubuntu installer or its alternative installer.
And 8GB is not particularly large for / (root). I use 25 or 30GB for partition and actually use about half  with Ubuntu and many applications, mostly smaller.

You should be able to follow the details here, just you do not need to copy files to /home, so skip those steps. It mostly will be adding new entry into fstab.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by bs892 on 2018-09-02
Thanks - all I had to do was edit /etc/fstab to mount the /home partition. Pretty cool, pretty easy. The thing that confused me about that page was the mention of rsync, so for anyone else wondering, that part can be skipped. I didn't need to move any data around to mount the existing home partition as home. Simple, of course. 8GB is sufficient; as long as I keep up on autoremove and autoclean, the partition doesn't run much past 4GB.

> **oldfred said:**
> Have not used Lubuntu installer or its alternative installer.
And 8GB is not particularly large for / (root). I use 25 or 30GB for partition and actually use about half  with Ubuntu and many applications, mostly smaller.

You should be able to follow the details here, just you do not need to copy files to /home, so skip those steps. It mostly will be adding new entry into fstab.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by oldfred on 2018-09-02
Glad it worked.
You can change to [solved], so others with same issue may find it.

---

