---
title: "mysql failed to start after upgrade"
date: 2023-07-27
forum: Installation &amp; Upgrades
---

### Post by leonidas300 on 2023-07-27
I upgraded mysql to 8 and now it fails to start.
I get this error in log file:
```

2023-07-27T13:28:04.630518Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.33-0ubuntu0.22.04.4) starting as process 10696
2023-07-27T13:28:04.642604Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
2023-07-27T13:28:04.955359Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
2023-07-27T13:28:05.450531Z 4 [System] [MY-013381] [Server] Server upgrade from '80031' to '80033' started.
2023-07-27T13:28:55.534053Z 4 [ERROR] [MY-013178] [Server] Execution of server-side SQL statement 'EXECUTE stmt; ' failed with error code = 1205, error message = 'Lock wait timeout exceeded; try restarting transaction'.
2023-07-27T13:28:55.535908Z 0 [ERROR] [MY-013380] [Server] Failed to upgrade server.
2023-07-27T13:28:55.536059Z 0 [ERROR] [MY-010119] [Server] Aborting
2023-07-27T13:28:56.710946Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.33-0ubuntu0.22.04.4)  (Ubuntu).


```

* The hosting server is on digitalocean droplet (1GB ram, 1CPU)

---

### Post by TheFu on 2023-07-29
I saw that the mysqlclient package was updated sometime this week when I patched this morning.

MySQL 8 changes many things. Find the v8 upgrade guide for mysql to see the required changes. [https://dev.mysql.com/blog-archive/upgrading-to-mysql-8-0-here-is-what-you-need-to-know/](https://dev.mysql.com/blog-archive/upgrading-to-mysql-8-0-here-is-what-you-need-to-know/) is one.  There are a bunch of changes.

---

