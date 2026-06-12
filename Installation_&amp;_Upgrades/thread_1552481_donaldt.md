---
title: "donaldt"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by donaldt on 2010-08-13
is there an Ubuntu 10.4 shut down and restart program?  I can't find one.  IMAC has a program that will shut down your computer and restart each day.  Surely linux could do the same?

---

### Post by Iowan on 2010-08-13
There is **cron** (and anacron). There's another - whose name escapes me at the moment - also for running scripts at predetermined times...

---

### Post by confused57 on 2010-08-13
> **donaldt said:**
> is there an Ubuntu 10.4 shut down and restart program?  I can't find one.  IMAC has a program that will shut down your computer and restart each day.  Surely linux could do the same?
Yes, and "Don't call me Shirley"(sorry, couldn't resist the quote from Airplane).

 I believe cron can do it for you, as Iowan mentioned:
[http://members.iinet.net.au/~herman546/p8.html#alarm_clock](http://members.iinet.net.au/~herman546/p8.html#alarm_clock)

Added: Cron or anacron should be able to shutdown your computer, but you may be able to set your bios to automatically start it:
[http://ubuntuforums.org/showthread.php?t=858838](http://ubuntuforums.org/showthread.php?t=858838)

---

### Post by wojox on 2010-08-13
> **Iowan said:**
> There is **cron** (and anacron). There's another - whose name escapes me **at** the moment - also for running scripts at predetermined times...

The at command?

---

