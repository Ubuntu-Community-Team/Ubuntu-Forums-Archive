---
title: "Error in repositories"
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by jana05 on 2012-03-08
Hello All, 

The update manager starts up and continues for sometime finding the headers and so on for a few minutes and then finds these error messages and is unable to update further. It fails to update.

What is the reason and how to work around, any solutions?

> 
W:Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Thanks in advance.

---

### Post by plucky on 2012-03-08
> **jana05 said:**
> Hello All, 

The update manager starts up and continues for sometime finding the headers and so on for a few minutes and then finds these error messages and is unable to update further. It fails to update.

What is the reason and how to work around, any solutions?



Thanks in advance.

Disable/Delete that PPA in Software Sources as it doesn't have a repository for Oneiric.

See [Here](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/)

Good Luck

---

