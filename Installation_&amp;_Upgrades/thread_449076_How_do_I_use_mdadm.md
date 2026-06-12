---
title: "How do I use mdadm?"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by Kazol on 2007-05-19
I have Feisty already installed on an 80GB HD. I want to setup software RAID-1 to the second identical 80GB HD; is this possible and how? I tried following all howto's but I want to configure RAID after installation, not during installation.

---

### Post by tormentum on 2007-05-20
I'm not sure how you'd go about setting up RAID-1 post installation, although I'm sure it's possible.  The problem I see however, is that RAID partitions usually need to be setup before you format the partition with your filesystem of choice.  There is a great HOWTO on installing a RAID-1 system during installation, but I see you've tried those already...

[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

---

### Post by Kazol on 2007-05-20
I'll try setting up RAID using the guide above on another computer. If I want to run a simple webserver with apache, how should I partition the 2x10GB HD? The guide says 500MB for swap, but how much should be left for / and /home?

---

