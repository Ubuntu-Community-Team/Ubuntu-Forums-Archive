---
title: "Help with an error when software updater is run."
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by cody7002002 on 2013-02-26
I just installed Ubuntu a few weeks ago, so there's a lot that I don't know. Today I went to run the software updater to see if there were any updates available and I received this message: "Failed to download repositor information" under details it says 

"W:Failed to fetch [http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."

How can I make this fix this so that I can run the updater as usual?

---

### Post by matt_symes on 2013-02-26
Hi

This guide tells you how to add sources to software-center.

Follow the steps but uncheck the sources that are giving you the problems. (the step before clicking the add button).

That should fix update-manager.

[http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu](http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu)

Kind regards

---

