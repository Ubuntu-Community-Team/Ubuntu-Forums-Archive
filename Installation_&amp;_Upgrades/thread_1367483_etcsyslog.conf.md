---
title: "/etc/syslog.conf"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by Skip Da Shu on 2009-12-29
After a rough upgrade that ended up being a fresh install of v9.10 into the previous v9.10 "/" partition... I'm back up and running just setting a few things back up.  I was going thru a backup file of my v9.04 /etc directory and noticed that in v9.04 I had a /etc/syslog.conf file.  I do recall setting up a logrotate.conf but don't think I mucked about with syslog.conf.  I don't recognize any fiddling by myself within the backuped up v9.04 syslog.conf file either.  However I don't find /etc/syslog.conf or man syslog.conf on the v9.10 system.  I am assuming the functionality has moved elsewhere in v9.10.  Anybody know where it went?

---

### Post by Trackieman on 2010-09-29
It's now /etc/rsyslog.d/50-default.conf

---

