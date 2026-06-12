---
title: "Stucked in the upgrading process from 7.04 to 7.10"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by jutirain on 2007-10-21
I'm upgrading ubuntu 7.04 to 7.10 follow the official guide

(using GUI tool rather than terminal)

However, it is the second time I stucked in the "Preparing the upgrade"

at "Fetching file 48 of 63"

Is it my network problem? (I can use firefox without any problem, however)

or the problem of server?

Anybody in the same situation?

---

### Post by maverick_mach on 2007-10-21
Well even am facing some similar trouble....
am upgrading from 7.04 to 7.10...th upgrade process runs smoothly an when fetching th files it gives me these errors...

Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/smproxy/smproxy_1.0.2-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/smproxy/smproxy_1.0.2-0ubuntu1_i386.deb) 403 Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-cards-data_2.20.0.1-0ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-cards-data_2.20.0.1-0ubuntu2_all.deb) 403 Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.20.0.1-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.20.0.1-0ubuntu2_i386.deb) 403 Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.20.0.1-0ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.20.0.1-0ubuntu2_all.deb) 403 Forbidden

Thse are because of th firewall in th university...jus 4 files are not able to fetch ...
an now i've downloaded them using an anonymous site but don't know where to copy them to...
Can nybody help me in this...I guess u got my problem...Basically i jus wanna know that where does ubuntu fetches th files for upgrade so that i can add these 4 files to that folder an continue with th upgrade process...

---

### Post by bluedragon436 on 2007-10-21
Well if you are having an issue using the GUI tool rather than the Terminal why not give it a try using the terminal and see if you still get stuck at that one point or at any point.  I will say I had a few scares as I was upgrading my computer when it got stuck at a few different places, but then after leaving it alone for a bit continued on, it just took  a bit longer than it could/should have...but all is well now...

---

### Post by vonderer on 2007-10-21
> **maverick_mach said:**
> don't know where to copy them to...
Can nybody help me in this...I guess u got my problem...Basically i jus wanna know that where does ubuntu fetches th files for upgrade so that i can add these 4 files to that folder an continue with th upgrade process...
Just install them yourself: sudo dpkg -i /path/to/package/package.deb
Or, if they all are in same directory: sudo dpkg -i /path/to/packages/*.deb

Also, you can put them in /var/cache/apt/archives and continue your update process. :)

---

### Post by bluedragon436 on 2007-10-21
Actually thinking about it why not go to the ubuntu website and do the upgrade from there??  I did that after having a few issue going thru other routes...and had not issues there!!!

---

### Post by shorai on 2007-10-23
Hi 
I am having the same Forbidden message (403) and have been for nearly a month.

I now have 98 packages to load , so doing it manually is not an option

I can firefox to the pages on the server - therefore firewall is not a problem - I have even tried stopping firestarter with no success.

Does anyone know how I can recover and get the upgrades going again?

    At this stage I cannot install any software and need to put some additional packages into my Ubuntu post haste.

    BTW, the 'latest' upgrade also reset my Java from JDK 1.6 to JRE 1.4 - most unfriendly

Thanks

---

