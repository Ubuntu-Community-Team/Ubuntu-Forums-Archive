---
title: "Upgrading to 11.04 with PPAs installed"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by mastablasta on 2011-08-08
I was just wondering if it would be safe to perform a system upgrade to 11.04 even if i have some PPAs installed.

For the most of them they are really not that important and i can just reinstall them. 

However there are two that might raise a red flag and these two are KDE PPA and Mozilla PPA (i am currently using 10.10 with upgraded KDE via PPA and also Mozilla upgraded to latest stable version).

---

### Post by sikander3786 on 2011-08-08
No one can guarantee a safe version upgrade.

I would at least recommend to purge the KDE PPA using 'ppa-purge' and then try upgrade so there aren't many dependency problems involved.

Mozilla PPA shouldn't cause problems but you can at least disable it before the upgrade and then re-enable when successful. If you happen to upgrade without purging the KDE PPA, at least disable it the same way.

---

