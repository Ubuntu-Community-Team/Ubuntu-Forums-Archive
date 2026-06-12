---
title: "inplace upgrade from 11.04 after GRUB restart  loop"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by scoutdubna on 2012-07-30
We have a Ubuntu server that is running 11.04 it has a 3 disk mirror. if we remove disk three and take it out (as a backup) this boots up fine (on identical hardware)

however every time we try to do "do-release-upgrade" it gets all the way to the point to restart fine.  on rebooting we see the Grub boot loader but as soon as it tries to load linux it instantly restarts and runs through the POST again.  there is nothing on the screen it just goes back to the POST

we are naturally nervious to run the upgrade on the real server as we don't want to rebuild it.  

I'm concerned its to do with the fact we are running on a degraded md array 

Any help regarding this would be helpful has any one seen this issue.

its not that the next distro dosen't like the hardware cause we have reinstalled 11.04 on a different disk in the system and ran through the in place upgrade fine.

---

