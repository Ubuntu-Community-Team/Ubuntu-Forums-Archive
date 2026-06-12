---
title: "upgrading over dialup"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Rumpty on 2006-06-20
Is it feasible for me to upgrade from Breezy to Dapper overnight  using a 56k dial-up connection? Specifically, about how long would it take, and is any terminal input required during the upgrade? 

Or maybe it is a crazy idea. Thanks.

---

### Post by glotz on 2006-06-20
I think that's crazy. It'd take a fortnight. And it would get interrupted and everything would go up in flames. Order the CD. For free. [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) (seems to be down at this moment)

---

### Post by nanotube on 2006-06-20
[QUOTE=Rumpty]Is it feasible for me to upgrade from Breezy to Dapper overnight  using a 56k dial-up connection? Specifically, about how long would it take, and is any terminal input required during the upgrade? 

Or maybe it is a crazy idea. Thanks.[/QUOTE]
well, a dapper upgrade will take about 600 (maybe even 700, but let's be optimistic) megs. at 56Kbps that will be about 120,000 seconds, or 33 hours or so. so, not overnight, no. but over 33 hours, maybe. :) 
but with dialup, you are better off ordering a cd from shipit (or even asking a friend with broadband to download an ISO for you - make sure to get the alternate cd, not the desktop, because it can be used for upgrades).

---

### Post by aysiu on 2006-06-20
If you insist on downloading a CD over dial-up (and I would definitely advise getting a CD for the upgrade, rather than just upgrading over the internet), make sure you get the Alternate Install CD and use bittorrent instead of a straight download.

Especially since you have such a slow connection, bittorrent will help you make sure the huge ISO you're downloading is more likely to download intact (without corruption).

Once you've burned the CD, pop it in your drive and ```
sudo apt-cdrom add
sudo cp /etc/apt/sources.list /etc/apt/breezy.list
kdesu kwrite /etc/apt/sources.list
``` Delete everything except the CD-ROM source you just added ```
sudo aptitude update
sudo aptitude dist-upgrade
``` Watch the sparks fly. And if the upgrade doesn't happen smoothly, at least you have a CD now that you can reinstall with.

---

### Post by Rumpty on 2006-06-20
Ok, it looks like I had better get the Alternate CD. I have previously bought the K(ubuntu) CDs from a local shop for a modest charge, so that seems to be the way to go again. Can I also do a clean install if necessary from the alternate CD?

---

### Post by aysiu on 2006-06-20
Yes, you can do a clean install from the Alternate CD. It's the same interface (text-based graphical installer) that Breezy, Hoary, and Warty.

---

### Post by Rumpty on 2006-06-20
Thanks everyone. Just have to make sure my supplier has the Alternate CD!

---

