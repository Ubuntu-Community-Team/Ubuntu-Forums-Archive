---
title: "Upgrade 9.04 to 9.10 Get Imminent Disk Failure"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by Charleyh on 2009-11-18
I have been using Ubuntu 9.04 for a little while with no problems. I tried the upgrade to 9.10. On first boot I get Imminent Disk Failure. I tried a clean install... same error. Does anyone know why 9.04 runs great & 9.10 gives me this issue? What changed??
CharleyH

---

### Post by Mark Phelps on 2009-11-18
Unfortunately, there seem to be more and more reports of 9.10 claiming disk errors and/or failing drives -- when neither is the case.

Suggest you boot into LiveCD of 9.04 and run fsck on your partitions.  If it reports no errors (as I suspect it will), then you are yet another of the victims of "false positive" reporting by 9.10.

Also, if you want a higher comfort level, go the website of your hard drive manufacturer.  They generally have downloadable diagnostic tools.  IF so, download and run those to see if their tools report any disk problems.  My guess will be that their tools will find your drive as being OK.

---

