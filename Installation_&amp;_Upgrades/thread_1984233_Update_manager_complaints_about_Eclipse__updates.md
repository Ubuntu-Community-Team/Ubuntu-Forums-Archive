---
title: "Update manager complaints about Eclipse  updates"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-05-21
I get following messages, when I start the Update manager:

W:Failed to fetch [http://ppa.launchpad.net/eclipse-team/debian-package/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/eclipse-team/debian-package/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/eclipse-team/debian-package/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/eclipse-team/debian-package/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/eclipse-team/debian-package/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/eclipse-team/debian-package/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


How to solve?

---

### Post by cortman on 2012-05-21
Do you use Eclipse?

Open up the Ubuntu Software Center, go to Edit>Software Sources. On the "Other Software" tab, uncheck the Eclipse repositories.

---

