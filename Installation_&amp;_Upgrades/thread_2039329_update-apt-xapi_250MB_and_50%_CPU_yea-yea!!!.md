---
title: "update-apt-xapi :250MB and 50% CPU yea-yea!!!"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by FSMaximeH on 2012-08-08
Kubuntu 32 bit 12.04 KDE 4.9
Hi there
Any idea to stop this bug that is around since 2007(!) and that no developer seems to be able to stop?

Recall:
update-apt-xapi is a process that start whenever it wants (usualy 10 -20 min after starting my netbook) and start to eat RAM up to 250 (about 25% of my laptop RAM...) with CPU at 90% for about 5 min..
I have found some posts on the web about it but was wondering what is the nowdays best solution to get the rid out of this stuff
When i want to remove apt-xapian-index it says it gonno remove muon...

It would be good if this bug can be solve (let's say within the next decade ?) because this is a reason why part of the user are kept away of ubuntu (I have seen so much user giving up with linux/ubuntu because their computer was "dead slow")

cheers

---

### Post by Zorael on 2012-08-08
**anacron** is set up by default to have it run once every week. If you want to disable it outright, just delete **/etc/cron.weekly/apt-xapian-index**. It may be enough to unset it from being executable (-x).

edit: okay, 5 minutes is a bit long, yeah. You could move it into **cron.monthly** if you just want to have it trigger less often.

---

