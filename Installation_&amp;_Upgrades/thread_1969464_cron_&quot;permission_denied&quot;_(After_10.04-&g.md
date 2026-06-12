---
title: "cron &quot;permission denied&quot; (After 10.04-&gt;12.04 u/g)"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by fergusg on 2012-04-30
None of my cronjobs run any more (neither for root nor for users).  /var/log/syslog shows:

```
Apr 30 09:22:01 goose CRON[6206]: Permission denied
```

but I can't see anything else. (I get this even with "trivial" cron entries like "* * * * * /bin/echo hello").  Restarting cron doesn't help.

anacron jobs are failing too with "unable to set uid to 0". 

/var/spool/cron/crontabs//* ownership look right <user>:crontab

(Possibly related, several log files are zero sized, e.g., /var/log/messages [syslog:adm])

---

### Post by fergusg on 2012-04-30
auth.log shows something interesting.  Dunno what it means, though...

Apr 30 09:21:01 goose CRON[6206]: PAM pam_parse: expecting non-zero; [...]

---

### Post by byronical on 2012-05-01
Same for me.
It would appear that for some files/directories under /var/log, that since the 12.04 upgrade, the ownership has changed from root:root to syslog:adm. This is why my cron jobs that run under root are now failing.
Not sure why the ownership changed though

---

### Post by fergusg on 2012-05-01
It appear that the problem is a dodgy libpam_mount.  Uninstalling that solved my problem.

[https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/927828](https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/927828)

This is for the cron issue, not the empty log files.  However, I have looked at 2 older Ubuntus (Heron) and they have ownership as syslog:adm so I think that's a red herring.

---

