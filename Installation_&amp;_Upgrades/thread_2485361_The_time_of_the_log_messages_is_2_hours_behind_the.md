---
title: "The time of the log messages is 2 hours behind the real and system time."
date: 2023-03-28
forum: Installation &amp; Upgrades
---

### Post by Hans_van_Leeuwen on 2023-03-28
On my new Ubuntu 22.04.2 system, the contents of the file /etc/timezone is 'Europe/Amsterdam'.
When I ask the current time with the command 'date', I get the real time in the 'CEST' time zone.
Last week the time was in the 'CET' time zone.
So the switch to 'daylight saving. works correct.
This morning I login at 8:30 AM, but the logon message in the file /var/log/auth.log has the time mark 6:30 AM.
Also in the file /var/spool/cron/crontab/root, should I subtract 2 hours from the intended time, to get the cron job started on the intended time.
I restarted the system and this morning, I execute 'systemctl restart rsyslog.service' but the time difference still occur.
 
How can I solve this time difference?

---

### Post by Hans_van_Leeuwen on 2023-03-28
The inode /etc/localtime was a symbolic link to the inode /etc/share/zoneinfo/Etc/UTC.
The inode /etc/localtime is now a symbolic link to the inode /etc/share/zoneinfo/Europe/Amsterdam.
After rebooting the system, the problem was solved.

---

