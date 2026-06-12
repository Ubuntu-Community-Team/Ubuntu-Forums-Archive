---
title: "MSI Wind - Suspend and Hibernate not working"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mintie on 2009-04-18
Just upgraded to Jaunty this morning, and everything updated cleanly without much fuss. Things seem to boot faster, and are generally more responsive. However - one show stopping bug, Suspend and Hibernate aren't working at all.

Both Suspend and Hibernate turn the screen off for a second, disconnect the wireless and then flash back on, and proceeds to connect the wireless again. Is anyone else experiencing similar issues/have a fix?

---

### Post by Zorael on 2009-04-18
I've been running Jaunty since alpha5 and I can hibernate/suspend on my Advent 4211, which is basically a rebranded Wind. I haven't tried since the release of RC though, so perhaps some updates broke it, or you're just experiencing some of the side-effects of upgrading.

I can't try it out right away, but I can try to suspend later today to try to replicate.

---

### Post by Mintie on 2009-04-18
Resolved! There was something I had put in my powersettings.sh that was giving me an error on jaunty but not on intrepid. Edited it out, and now all is well!

---

