---
title: "W: Failed to fetch http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu/dists/lucid/main/bi"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by go4emperor on 2010-09-14
Hi there:
Somehow my repository got screwed up, I get following message when i try to update:

...

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.



Plz help this newbie

---

### Post by plucky on 2010-09-14
> **go4emperor said:**
> Hi there:
Somehow my repository got screwed up, I get following message when i try to update:

...

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.



Plz help this newbie

Open **System > Administration > Software Sources > Other Software**   and un-tick those PPA sources as they don't seem to be valid.

Reload the sources and see if you get the same problem.

If that fixes it then delete them from "Software Sources".

Where did you get the information to install those PPA's?

Do you really need them?

---

### Post by go4emperor on 2010-09-14
Cool man!

Thanks a lot. .. ...it worked.

Actually I am not sure from where I got those repositories - as I was constantly updating my distro using various tips on differnt forums. and when i tried to look back I couldnt find which application needed that.

But thank a millions to help me! I was a lot panic with my mischief!!

---

