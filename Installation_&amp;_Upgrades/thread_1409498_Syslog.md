---
title: "Syslog"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by mimor on 2010-02-17
I've got my router set up to log to a logserver running syslog.
The logserver is configured to accept external logsrepors with
/etc/init.d/sysklogd containing:
```
SYSLOGD="-r"
```

Now I want to add rules to /etc/syslog.conf so that those reports go to /var/log/router.log

The files are created, but I can't figure out how to have syslog "recognize" the packages it gets from the router.
But how do I do this?

Should this be something like:
```
router.crit /var/log/router.log 
```

---

