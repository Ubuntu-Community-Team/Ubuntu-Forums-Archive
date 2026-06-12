---
title: "backuppc 3.3.0-1ubuntu1 &quot;no ping response&quot; for localhost"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by DrJohn999 on 2014-08-03
Fresh install of backuppc 3.3.0-1ubuntu1 under 14.04 server; with no changes to the configuration, as a test ran full backup on host = localhost (just the /etc directory is selected by default). Backup fails with "no ping response." Able to 
```
ping -c 1 localhost
``` as backuppc user.

The original /etc/backuppc/config.pl file includes:
```
$Conf{PingPath} = '/bin/ping';
$Conf{Ping6Path} = '';
```

Solved by inserting /bin/ping6 :
```
$Conf{PingPath} = '/bin/ping';
# inserted '/bin/ping6' for default '':
$Conf{Ping6Path} = '/bin/ping6';
```
After backuppc restart, ping on the localhost host no longer fails.

---

