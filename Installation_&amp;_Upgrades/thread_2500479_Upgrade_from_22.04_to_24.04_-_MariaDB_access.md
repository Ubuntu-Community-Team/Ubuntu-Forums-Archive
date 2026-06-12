---
title: "Upgrade from 22.04 to 24.04 - MariaDB access"
date: 2024-09-03
forum: Installation &amp; Upgrades
---

### Post by asai on 2024-09-03
I have upgraded my server from 22.04 to 24.04. (do-release-upgrade)
After the upgrade, I don't have access to my database server.
It works fine from my webpages when using localhost, but I have a program that access the database from outside (internet).
Is there any changes in the connection to the database in 24.04?
As far as can see, theres no change in the database configuration.

Edit:
Checked the syslog file, and found theese 2 lines when trying to access the database:
```

2024-09-03T15:06:13.625572+02:00 server1 mariadbd[1502]: 2024-09-03 15:06:13 3584 [Warning] IP address '62.92.121.131' has been resolved to the host name '131.121.92.62.static.cust.telenor.net', which resembles IPv4-address itself.
2024-09-03T15:06:13.729695+02:00 server1 mariadbd[1502]: 2024-09-03 15:06:13 3584 [Warning] Aborted connection 3584 to db: 'Regnskap' user: 'root' host: '62.92.121.131' (Got an error reading communication packets)

```

---

