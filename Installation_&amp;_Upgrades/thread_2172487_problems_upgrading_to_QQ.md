---
title: "problems upgrading to QQ"
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by alexscr on 2013-09-05
Hi folks each time i try to upgrade i get the following msg and the upgrade craps out when i acknowledge the msg by clicking on "close" - the "network" appears to be working fine ... Any ideas please ?? - alex
{Error during update 


A problem occurred during the update.This is usually some sort of network problem, please check yournetwork connection and retry.


W:Failed to fetchhttp://au.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources 404  Not Found 
, W:Failed to fetchhttp://au.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources 404  Not Found 
, W:Failed to fetchhttp://au.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources 404  Not Found 
, W:Failed to fetchhttp://au.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources 404  Not Found 
, E:Some index files failed todownload. They have been ignored, or old ones used instead.}

---

### Post by coffeecat on 2013-09-05
You have several problems:

1 - Maverick - Ubuntu 10.10 - has been end-of-life for over a year and the repositories for it are closed.

2 - To upgrade to Quantal - 12.10 - you would need to upgrade in four steps, 10.10 -> 11.04 -> 11.10 -> 12.04 -> 12.10. Except that 11.04 and 11.10 are also end-of-life so the normal upgrade process won't work.

It is possible to upgrade eol versions by using the old-releases repositories. See here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Unfortunately that page is very neglected and I only link to it to give you an idea of the principle of eol upgrades. It doesn't list the upgrade path you need to take and there are a couple of other things you need to do that are not detailed there - at least last time I looked at it in detail.

I suggest you think about doing a fresh install of the latest version, 13.04. Backup your personal data first, of course. Even if you could find another wiki page that described accurately how to do the upgrade path you need, it's a long one, with a lot of downloads, and has the potential to go wrong.

---

