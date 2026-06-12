---
title: "pepper flash non-free"
date: 2015-01-28
forum: Installation &amp; Upgrades
---

### Post by michael-piziak on 2015-01-28
From a previous post, I discovered that pepper-flash non-free is no longer available for 12.04 lts.

Anyone know when it will be [or why it currently is not] ?

link to previous post:  [http://ubuntuforums.org/showthread.php?t=2255393&highlight=google+chromium](http://ubuntuforums.org/showthread.php?t=2255393&highlight=google+chromium)

---

### Post by deadflowr on 2015-01-28
Pepperflash has never been available for 12.04 in the default repos.
You've always needed to add a ppa to get it.
[https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash?field.series_filter=precise](https://launchpad.net/~skunk/+archive/ubuntu/pepper-flash?field.series_filter=precise)

What did happen was that the chromium project dropped the old plugin api (the NPAPI plugin, that uses the normal/regular/*? flash) and so chromium was left out in the dust. The release of 14.04 came after that happened, b ut 12.04 was left out in the cold.

---

