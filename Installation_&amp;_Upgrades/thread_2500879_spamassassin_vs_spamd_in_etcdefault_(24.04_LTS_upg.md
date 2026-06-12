---
title: "spamassassin vs spamd in /etc/default (24.04 LTS upgrade)"
date: 2024-09-14
forum: Installation &amp; Upgrades
---

### Post by matthys on 2024-09-14
This is the 2nd time I notice something strange after upgrading to 24.04 LTS and I guess this is due old config not migrated and/or removed.

I got these files and wonder what is what:
/etc/default/spamassassin
/etc/default/spamd

Does this mean all is migrated/moved to /etc/default/spamd?
Because I have some specific setting in /etc/default/spamassassin and they are (ofcourse) not in /etc/default/spamd
Which one is used? I guess spamd.

There seems to be no spamassassin running, but there is spamd:
systemctl status spamd
&#9679; spamd.service - Perl-based spam filter using text analysis
     Loaded: loaded (/usr/lib/systemd/system/spamd.service; enabled; preset: enabled)
     Active: active (running) since Sat 2024-09-14 17:59:50 CEST; 4s ago
   Main PID: 733954 (spamd)
      Tasks: 1 (limit: 6352)
     Memory: 87.3M (peak: 87.5M)
        CPU: 2.358s
     CGroup: /system.slice/spamd.service

For example in the /etc/default/spamassassin I got the cron job, which is NOT in the spamd:
```
# Cronjob
# Set to anything but 0 to enable the cron job to automatically update
# spamassassin's rules on a nightly basis
CRON=1
```

As it seems it's using spamd, does this mean no updates of the rules?

Thanks,
Matthijs

---

