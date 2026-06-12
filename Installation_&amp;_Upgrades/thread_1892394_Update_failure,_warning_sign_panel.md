---
title: "Update failure, warning sign panel"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by evez on 2011-12-07
[B][B]ASUS laptop, Ubuntu 10.10 Maverick Meerkat

Since yesterday I there's a warning sign on my panel saying: 

The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this item and then selecting "check for updates" and check if some of the listed repositories fail.

I already changed the repository so that shouldn't be the problem. Neither shud the connection be.

I'm not familiar with updating via synaptic and didn't succeed. I then tried to update via terminal and after long line of listings (Ign [http://ubuntu.idrepo.or.id/ubuntu/](http://ubuntu.idrepo.or.id/ubuntu/) maverick-updates/multiverse Translation-en_US) finally is says:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/barraudmanuel/vpnautoconnect/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/barraudmanuel/vpnautoconnect/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/barraudmanuel/vpnautoconnect/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/barraudmanuel/vpnautoconnect/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

I have no idea how to deal with this problem and am afraid I will get into trouble with repeated lack of updates. As you may guess I'm pretty crap with this system but wanna try so hard.

thanks mates!

---

### Post by jerrrys on 2011-12-09
Your launchpad source for barraudmanuel seems to be no longer available.  Try removing it from software sources.

Open a terminal and enter:

sudo gedit /etc/apt/**sources**.list

then navigate to the entry:

 /barraudmanuel/vpnautoconnect/ubuntu/dists/maverick/main/source/Sources.gz

and just comment it out by adding a **#** mark at the beginning of that line or lines (you may have two entries).

If you would like verification first, please post your sources list.

---

