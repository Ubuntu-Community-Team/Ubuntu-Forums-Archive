---
title: "Software center problems"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by Fredo_p on 2013-05-06
Oh thank goodness. I was looking for info on this issue. I always use Software Updater, but since the 13.04 update for Lubuntu, I've had the same issue. When I run it, I get the "Failed to download repository information (check your internet)". But when I click the OK button, it goes straight to the next window, whether it be updates or the "No software updates are available."

I tried [COLOR=#000000]ping -c 5 [/COLOR][http://us.archive.ubuntu.com/ubuntu/dists/raring/main/](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/)[COLOR=#000000] && traceroute [/COLOR][www.ubuntu.com]("http://www.ubuntu.com/"), but I get the error```
 ping: unknown host [http://archive.getdeb.net/ubuntu/dists/raring/main/](http://archive.getdeb.net/ubuntu/dists/raring/main/)
```.

Any idea what I can use to see where the errors are for me? I am running Lubuntu 13.04 on a Toshiba Satellite A135 laptop.

---

### Post by ibjsb4 on 2013-05-06
A raring source for getdeb.net does not yet exist.  You need to uncheck it in your software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by matt_symes on 2013-05-06
Posts moved into new thread as requested.

---

