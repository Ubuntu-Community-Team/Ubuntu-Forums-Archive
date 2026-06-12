---
title: "Troubles with Ubuntu 16.04"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by lusbyclark2 on 2016-10-16
When Ubuntu 16.04 became available, I upgraded both my desktop PC and my laptop.  Things went quite well with both upgrades.  Some weeks later Canonical offered additional upgrades to 16.04 and I dutifully performed the upgrade.  However, this time It failed to work on the first try and I had to go back and try a second time.   A month or so later, my son tried upgrading his desktop from 14.04 to 16.04 and his desktop operating system suffered an abject failure.  It turned out to be some graphics drivers were somehow damaged in the upgrade.  Once these drivers were "re-reinstalled" it finally began working. 

As I look around on this forum, I see what I take to be lots of complaints regarding difficulties with upgrading to 16.04 and even 16.10.  Am I misinterpreting what I am seeing here, or is this the general understanding?  I see that Canonical is now offering a new round of extensive upgrades to 16.04.  I am reluctant to perform this upgrade.  Is this one safe, or should I wait a little longer to allow it to mature?

---

### Post by oldfred on 2016-10-16
When you upgrade from one version to another you must first remove all ppa and any proprietary drivers. They conflict with upgrade process.
Then after upgrade just reinstall (if available) ppas and proprietary drivers.

The regular updates should not cause issues, unless you installed proprietary drivers directly from a vendor. Then the are only incorporated into the kernel with that install and then with every update you have to rerun dpkg to include them. Always best to install proprietary drivers from Ubuntu repository or if video from the supported ppa site.

I used to upgrade all the way from 6.06 to 9.04 (32 bit). And had issues, primarily with video.
But then to install 64 bit I had to do a new clean install, but installed in another 25GB / (root) partition and separated data from system.
That went so well I now always install to a new 25GB / partition, keeping old one just in case I missed something I should have backed up.
My main working install is always most current LTS, but may have older & newer installs also on system.

---

