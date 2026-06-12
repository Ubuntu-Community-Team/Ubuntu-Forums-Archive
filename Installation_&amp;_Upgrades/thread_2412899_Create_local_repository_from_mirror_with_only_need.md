---
title: "Create local repository from mirror with only needed packages"
date: 2019-02-18
forum: Installation &amp; Upgrades
---

### Post by sampsonats on 2019-02-18
I would like to create a local Ubuntu repository that only contains the packages that I need.  It would be perfect if I can start with a machine that's configured as the golden master and produce a list of the packages that have been loaded on the golden master, then use that list to populate my local repository.  I've looked at apt-cache and similar that creates a proxy server that caches all the content that is requested.  I would like to have more control over the repository.  I also looked at Aptly.  It is really nice but doesn't seem to have a way to extract installed package information from a server and apply it as a filter to populating a repo.

I'd greatly appreciate any ideas!
Thanks,
Todd

---

### Post by Tadaen_Sylvermane on 2019-02-20
Apt-cacher-ng is what you want. Caches packages locally. Only need to download them once, unless an updated version is available. I use it at home, greatly speeds up my updating on my lan.

Other than scripting something I think this is your best option.

---

