---
title: "Possible boot probs"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by charlieuk on 2005-07-14
I put this in the Hoary forums not the warty 1 so here it is 

Maybe I get a better responce
I have rtecently installed ubuntu onto a machine with an

intel celron 750

64m pc133

20gb maxtor hdd

on boot I get 3 fatal errors which are :-

mod probe: FATAL: error inserting hw_ random /lib/modules/2.6.8.1-3-386/kernel/drivers/char/hw_random.ko): no such device

mod probe: FATAL: error inserting pciehp( /lib/modules/2.6.8.1-3-386/kernel/drivers/hotplug/pciehp.ko): operation not permitted

mod probe: FATAL: error inserting shpchp( /lib/modules/2.6.8.1-3-386/kernel/drivers/hotplug/shpchp.ko): operation not permitted

then error 

*ror* temp failure in name resolution [fail] in red

and on close down another error message

*gnome display manager not ruinning

when finally booted the system responce time can be likened to a min spec 486 running win98

any ideas anyone ??


also where do I find MBS so that I can enable windows networking ???

---

### Post by badrinarayan on 2005-07-14
For the "FATAL errors", refer to [http://ubuntuguide.org/4.10/index.html#modprobefatalerror](http://ubuntuguide.org/4.10/index.html#modprobefatalerror)

I think synchronizing clock causes the second error. So disable it as in [http://ubuntuguide.org/4.10/index.html#modprobefatalerror](http://ubuntuguide.org/4.10/index.html#modprobefatalerror)

Regards
Badri

---

### Post by charlieuk on 2005-07-15
cheers Badri when I learn how to get to script in this environment I'll try that :)

---

