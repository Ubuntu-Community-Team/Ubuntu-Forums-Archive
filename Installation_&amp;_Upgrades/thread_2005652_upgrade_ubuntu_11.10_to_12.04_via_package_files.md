---
title: "upgrade ubuntu 11.10 to 12.04 via package files"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by mohitgorhe on 2012-06-18
Hii......

I want to upgrade my ubuntu 11.10 computer to latest version 12.04 .. using package folder.
I had found too but it seems that i will need to get repositories one by one which is quite frustratring tiring.... 

Any help is appreciated...

Plz help ........

---

### Post by gnusci on 2012-06-18
Use the online upgrade or download the latest version and use the upgrade option.

---

### Post by shubham1 on 2012-06-18
> **mohitgorhe said:**
> Hii......

I want to upgrade my ubuntu 11.10 computer to latest version 12.04 .. using package folder.
I had found too but it seems that i will need to get repositories one by one which is quite frustratring tiring.... 

Any help is appreciated...

Plz help ........
which package folder are you talking about

---

### Post by TideMan on 2012-06-18
I'm migrating from 10.04 to 12.04 by upgrading, and I've passed thru 10.10, 11.04 and onto 11.10 OK. But now I've got 11.10 and it's completely different to anything before and I'm lost.

Where is the upgrade facility in 11.10?
I can't find it anywhere.  :(

---

### Post by Frogs Hair on 2012-06-18
An upgrade would be done via the update manager in 11.10. Look in update manager > settings and make sure it set to check for new releases. If that fails. ```
sudo apt-get update && sudo apt-get upgrade
``` ```
sudo do-release-upgrade
``` Note: The synaptic package manager is no longer a default package and will need to be installed in 11.10 and 12.04.

---

