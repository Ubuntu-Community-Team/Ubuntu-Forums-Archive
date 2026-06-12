---
title: "Having trouble updating in the software center"
date: 2015-11-18
forum: Installation &amp; Upgrades
---

### Post by kevin192 on 2015-11-18
I keep getting this error, preventing me from updating. Any way to fix it?

W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Kinshuk_Lahiri on 2015-11-18
The urls you have mentioned doesn't exist on the server and that's why i gives the message 404.

---

### Post by kevin192 on 2015-11-18
How do I get rid of those urls?

---

### Post by QIII on 2015-11-18
It is likely that the PPA is either no longer maintained, has no candidate for your release or has been withdrawn.

PPAs are not official and there are no guarantees associated with them.  

Disable the PPA in your sources and attempt to update.  You may de-select them in the Software Center.

---

### Post by kevin192 on 2015-11-18
Fixed! Thank you. :)

---

