---
title: "Failed to download repository information"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by Shenghai on 2013-04-11
Hi,
I am getting an error when I attempt to upgrade ubuntu 12.10.
Here is the code - 
```
 W:Failed to fetch http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found, W:Failed to fetch http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```
Is there a solution?
Thanks.

---

### Post by ibjsb4 on 2013-04-11
There is no ubun-tor ppa for quantal.

[http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/)

Remove it from software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

