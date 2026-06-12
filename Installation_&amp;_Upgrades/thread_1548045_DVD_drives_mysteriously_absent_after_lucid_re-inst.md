---
title: "DVD drives mysteriously absent after lucid re-install"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by skewray on 2010-08-07
I recently re-installed lucid on a machine with two working DVD writers, one SATA, the other IDE.  After the re-install, neither drive appears to be recognized.  Putting an blank CD into either used to cause a pop-up that would ask me if I want to run k3b, but now it doesn't.  If I use an external USB DVD writer, I do get that pop-up.  Sadly my external USB DVD writer apparently writes unreadable disks, so it is not part of a long-term solution.

Any suggestions?

Brian

---

### Post by skewray on 2010-09-08
bump

---

### Post by rotave on 2010-09-08
Have you tried putting a cd/dvd in one of the drives (can be a blank cd/dvd) while running Ubuntu and then rebooting the machine. Upon reboot the cd/dvd drive might be recognised. I have this problem sometimes and this "fixes" it.

---

### Post by skewray on 2010-10-10
It turns out that it you have two dvd drives, the stupid installer makes one /dev/dvd1 and the other /dev/dvd2.  It doesn't make any links at all for /dev/dvd, so virtually no programs on the system can find the dvd drives.  Making a new link in /dev doesn't fix the problem, since /dev is recreated every time the machine boots.  I suppose the solution is to make a link in rc.local.

---

