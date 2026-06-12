---
title: "Kubuntu 12.04 Super Slow"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by Jack the R on 2012-05-10
Fresh install with everything upgraded on an [Asus R1e-B1](http://reviews.cnet.com/tablets/asus-r1e-b1-core/4507-3126_7-32779072.html) with 4 gigs of ram.

The problem is a variation of the old cpu resource usage problem.  The cpus are constantly under massive load when there should be minimal load.  It takes a terminal over thirty seconds to load with no programs running.

I've disabled all the akonadi, nepomuks and strigi, to no effect.

It appears regular processes are the culprit this time, somehow using more cpu than they should.  I've seen xorg @ 50% cpu, ran system monitor and it took up 70% cpu . . .  

I've done all I know to do, need help.

---

### Post by daisyflower on 2012-05-10
This forum post might help, "Something to do with having an old database that's gone through various upgrades seems to cause this problem, I think." - [https://bbs.archlinux.org/viewtopic.php?id=134567&p=2](https://bbs.archlinux.org/viewtopic.php?id=134567&p=2) (post 27)

---

### Post by Jack the R on 2012-05-11
Good try, but deleting ~/.kde4/share/apps/nepomuk didn't help.  Virtuoso isn't showing up i top.

Last night I was thinking it could be a problem with the intel graphics driver, but I haven't gotten anywhere with that angle yet.

---

