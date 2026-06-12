---
title: "Cannot upgrade from 14.04 lts to 16.04.4 LTS due to DVD distribution name mismatch"
date: 2018-06-20
forum: Installation &amp; Upgrades
---

### Post by wheresthechocolate on 2018-06-20
Hi,

I am trying (and failing) to upgrade from 14.04 LTS to 16.04.4 LTS however have got stuck as the update manager wants a specifically named dvd to be inserted. It states it s looking for - Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228) however the distribution that is available to download is ubuntu-16.04.4-desktop-amd64 .

Having burnt a dvd with the ubuntu-16.04.4-desktop-amd64.iso the update manager is ignoring it insisting it needs Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228) . But they are the same, aren't they?

If I try and rename the iso file to be Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228) the actual distribution remains ubuntu-16.04.4-desktop-amd64 so burning another dvd will just be a waste of plastic.

I thought I could just open the ISO with archive manager,or link to the iso, but neither option is working as the update manager is looking for a differently named distribution.

I do not want to do a fresh install as I run a multi boot system and am concerned I will get something wrong and overwrite one of the other OS's.

Can someone tell me how I can get the update manager to use the ubuntu-16.04.4-desktop-amd64.iso, or where the Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228).iso is and how I can link to this, so I don't use yet another dvd?

Many thanks.

---

### Post by kc1di on 2018-06-20
At this point I don't have an answer for this.  But I would do a backup of all important data to external source and do a complete new (fresh) install of 16.04 or better yet 18.04. 
Good luck.

---

### Post by oldfred on 2018-06-20
It may be you have get updates from DVD in your update settings, System Settings, Software & updates.
System wants you to have fully updated before you upgrade. And you need to un-install any proprietary drivers and ppas or upgrade may fail.
You should also houseclean old cruft like log files & old kernels or they will stay forever as updates in new install will not know they are there.

Better just to follow kc1di's suggestion of new install and restore data & settings from you regular backup.

---

