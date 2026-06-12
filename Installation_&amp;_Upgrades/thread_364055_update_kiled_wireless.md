---
title: "update kiled wireless"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by eppoh on 2007-02-17
Just did the latest update to Edgy as requested in the updates notifier , When I restarted, my wireless card was no longer recognized. I rebooted again into the previous kernel and it runs okay. 
How do I find out what I loaded that killed it and fix it?

---

### Post by eradicator on 2007-02-23
I had the same issue with a Broadcom 1390 card using ndiswrapper. I dug around a little to see if there was an obvious/simple solution.

The solutions offered were:
Go through the same steps initially and reinstall ndiswrapper + wifi driver.
   -Not sure if that applies for you or not.
   -Someone said that the update drops an older version of ndiswrapper over whatever was there... 

Uninstall that latest kernel update.

Boot from the older kernel until there is another kernel update that may address the issues.


I went through the reinstall process for ndiswrapper + wifi driver. Not perfect, still cuts out after a while, but it is better than it was.

HTH   :-?

---

