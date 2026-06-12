---
title: "Issues with /etc/init.d"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by nits_555 on 2006-08-30
Hi,

I may have accidently deleted /etc/init.d folder. Screen dump of the normal bootup is as follows:

--------------------------------------------------------------------
INIT: cannot execute "/etc/init.d/rcS"
INIT: Entering runlevel: 2
INIT: cannot execute "/etc/init.d/rc"
(Blinking cursor)
--------------------------------------------------------------------

On trying to bootup in recovery mode:

-----------------------------------------------------------------
INIT: version 2.86 booting
INIT: cannot execute "/etc/init.d/rcS"
root@(none):~#(Blinking cursor)
root@(none):/etc# cd init.d
bash:cd:init.d: no such file or directory
-----------------------------------------------------------------

Apart from re-installation of ubuntu dapper (I have way too much programming setup on my current system, to even think of re-installing), can any of us please suggest a workaround?

Thanks,
Nitin.

---

### Post by FIONEX on 2006-08-30
Try a repair installation!

---

### Post by taurus on 2006-08-30
There is a crap load of stuff in /etc/init.d so I am not sure whether there is an easy way to recover it!!!  Probably best to back up important stuff and reinstall the whole thing.  My recommandation is to limit yourself with the sudo command and make sure you know what you are doing with the sudo...

---

