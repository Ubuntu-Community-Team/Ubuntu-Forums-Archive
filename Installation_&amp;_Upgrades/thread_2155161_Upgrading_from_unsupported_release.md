---
title: "Upgrading from unsupported release"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by xeon927 on 2013-06-17
Hi there!

Just earlier this evening, I logged into my offshore server and noticed something: it was still running Ubuntu 11.04.

I went to upgrade, but of course, all the packages 404'd, because the sources had changed. Long story short, I managed to correct the sources to the old archives, and get update-manager-core installed, so that I could run do-release-upgrade.

I noted that by using do-release-upgrade, I would need four upgrades to get to the newest version. Am I correct in thinking this? (ie, 11.04 -> 11.10, followed by 11.10 -> 12.04, then 12.04 -> 12.10, and finally 12.10 -> 13.04)

While talking to a friend at the same time as thinking whether or not to do this tonight or tomorrow morning, he said that the way he upgraded a Debian system in the past was by just changing the sources in /etc/apt/sources.list to point to the distro that he was upgrading to, followed by performing an apt-get dist-upgrade.

My question is this: Is it better to go through with the four iterations of do-release-upgrade, or should I just go through with my friend's advice with changing /etc/apt/sources.list (and if yes, is this a safe method of upgrading?)?

Thanks!

---

### Post by Frogs Hair on 2013-06-17
Hello and Welcome,

At least for the Desktop there are huge number of package changes so, just changing sources would be more of a crap shoot than the upgrades. An upgrade to 12.04 would make the most sense for a server because it has 5 year support (2017) and the interim releases such as 13.04 are down to 9 months of support. The next LTS release is 14.04 which will also have 5 year support.

---

### Post by xeon927 on 2013-06-17
With this being Ubuntu Server, would that make much difference? Or are there still too many packages that could break through just changing sources?

Also, I think I might just stick to the LTS releases. All three of my other servers use 12.04 LTS. This is the only server that worked well enough for me to set it and forget it, missing the time to upgrade. :P

---

### Post by Frogs Hair on 2013-06-17
Of course there are fewer packages with sever , but if you brick it you will have to re-install . The recommended method is to upgrade to the next version and you already have an end of life upgrade on your hands because the 11.04 repository is closed. I would preform a clean installation if possible. See the link for EOL upgrades. 

EOL Upgrades:[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

