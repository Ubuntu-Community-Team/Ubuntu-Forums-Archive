---
title: "Upgrade to feisty from cd or belnet server?"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by Tiftof on 2007-03-16
Hey,

I would like to try Feisty and I want to upgrade my current edgy setup. I read that it is advised to use: gksu “update-manager -c -d”. But can I change the sources it uses to update my edgy install? I am on an university isp and downloading from belnet server isn't counted in our downloading limit. So it would be great to update from there, or from a cd... Is this possible?

Thanks

---

### Post by Tiftof on 2007-03-18
After fooling around I got it to upgrade using the belnet servers by only adding this line into the sources.list and commenting everything else out:

deb [ftp://ftp.belnet.be/packages/ubuntu/ubuntu](ftp://ftp.belnet.be/packages/ubuntu/ubuntu) feisty main

During the upgrade process it will add a line for the ubuntu.com repository but won't comment out the belnet one. Once downloading the upgrades, it will use the belnet server.

---

