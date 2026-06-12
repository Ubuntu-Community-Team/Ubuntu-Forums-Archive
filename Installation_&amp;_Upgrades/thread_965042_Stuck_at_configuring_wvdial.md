---
title: "Stuck at configuring wvdial"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by stringkarma on 2008-10-31
I am almost through with the upgrade to intrepid and the updater has been stopped at configuring wvdial for a long time. Is there some way to skip this?
What should I do should this continue?

Thanks

---

### Post by vorgusa on 2008-10-31
I have the same problem... but it might be the last program upgraded.. anyone have  solution.. I am about to click exit and restart the comptuer.

---

### Post by vorgusa on 2008-10-31
I just killed the process since I do not use modems anyways and the install kept going

ps -e | grep wvdialconf

to get the process number

and 

sudo kill "the process number"

---

