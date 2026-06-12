---
title: "Update Manager Issues HELP!"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by andycastille on 2012-04-20
When I check for updates in the Update Manager or use "sudo apt-get update" I get the following:
```
W:Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```I am running the latest 12.04 beta.

---

### Post by jadtech on 2012-04-20
seems to be going around seems update manager is broken sort of , you can go into settings and change  the provider.

go to terminal type in sudo apt-get update

the some indel files failed to down load this error has been there for nearly a week now not sure how to get rid of that but the manager seems to still be working

---

### Post by andycastille on 2012-04-20
Thanks! I had tried sudo apt-get update, and the same error opens. Just glad to know it's their fault and not mine, and that hopefully they will fix it soon. At least before 12.04 comes out for good!

---

