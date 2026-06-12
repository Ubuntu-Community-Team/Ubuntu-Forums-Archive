---
title: "Which program update the file /var/lib/update-notifier/updates-available?"
date: 2016-01-27
forum: Installation &amp; Upgrades
---

### Post by Hans_van_Leeuwen on 2016-01-27
Hi All,

Which program/script update the file "/var/lib/update-notifier/updates-available"?
In this file is written how many packages-updates are available.
E.g. "7 packages can be updated."
Is the program/scripts that update that file started by "/etc/cron.daily"?
I don't see the file modification time back in "/etc/crontab" as a time that a program/script is started.

---

### Post by steveo314 on 2016-02-01
The update manager is its own entity. Has its own settings. cron is for you to define auto jobs.

---

