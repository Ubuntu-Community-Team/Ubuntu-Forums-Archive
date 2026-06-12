---
title: "Backup system"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by sagivegh on 2007-12-13
Hi,

Is there anyway, or simple program that can backup all the linux system and restore it?

thanks
Sagi

---

### Post by psusi on 2007-12-13
Yes, it's called tar.

sudo tar czf backup.tar.gz --exclude='/proc/*' --exclude='/sys/*' --exclude='/tmp/*' --exclude='/dev/*' --exclude='/var/cache/*' /

Will backup all of the important parts of the system, ignoring things like tmp files and cached packages.

I have a little script set up to perform weekly full backups and daily incremental backups and have cron run it automatically every night at 1 am.

man tar for more info.

---

