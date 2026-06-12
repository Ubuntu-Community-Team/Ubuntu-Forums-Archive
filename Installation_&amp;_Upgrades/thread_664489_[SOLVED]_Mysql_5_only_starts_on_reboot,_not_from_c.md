---
title: "[SOLVED] Mysql 5 only starts on reboot, not from cold start?"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by merrydown on 2008-01-11
I am running Ubuntu Gutsy Gibbon.  On a reboot mysql5 loads up integrated into php5 nicely.  Why is it that from a cold start php5 works but mysql5 doesn't start?  I get that unknown function pconnect error.

I would be glad to post any supporting information that would help...  I just don't get it.

If I need to do a reinstall of php5 including mysql5 (which I thought I had - but could have made mistakes) I can, though I'd be keen to preserve some of my php.ini settings.

Please help!  Thanks!

Jim :confused:

---

### Post by merrydown on 2008-01-20
The problem is solved.  The system wasn't recognising the hardware raid built into my server and was alternating between the two disks with almost identical content at boot time.  Now I have installed dmraid (and fixed the many disk errors that occurred at the time) the problem has not recurred.  Shame dmraid isn't part of the original installation by default!

Jim

---

