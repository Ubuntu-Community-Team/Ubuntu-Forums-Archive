---
title: "Dist-upgrader-all only in proposed?"
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by ben133 on 2015-01-18
I have been maintaining a local mirror for a while using apt-mirror and some rsyncs in a script. To execute "do-release-upgrade" on my local mirror I found I needed to separately download the dist-upgrader-all folder from dist/<ubuntu codename>-updates/main/ outside apt-mirror command in postmirror.sh. 

With the release of utopic I noticed that the folder dist-upgrader-all never left <ubuntu codename>-proposed. Is this the new pattern for ubuntu releases, or is the dist upgrader for utopic still considered under testing?

I only ask because normally I do not mirror proposed since it is a testing part of the mirror and I don't use the packages considered still under test.

Thanks in advance,
Ben

---

