---
title: "Upgrade to 20.04 killed mysql"
date: 2020-11-27
forum: Installation &amp; Upgrades
---

### Post by ian dobson on 2020-11-27
Hallo,

I've just attempted to upgrade my ubuntu/mythtv backend server to 20.04 and something has gone really wrong with mysql. After upgrading mysql doesn't start anymore. 
Looking through the error log  /var/log/mysql/error.log I can see that sys/sys_config is missing but the sql update is failing:-

```
2020-11-27T16:57:50.818836Z 4 [ERROR] [MY-013178] [Server] Execution of server-side SQL statement '-- Copyright (c) 2018, 2019, Oracle and/or its affiliates. >
2020-11-27T16:57:50.821771Z 0 [ERROR] [MY-013380] [Server] Failed to upgrade server.
2020-11-27T16:57:50.822358Z 0 [ERROR] [MY-010119] [Server] Aborting
```

I've attached to full log.

Is there an easy way to correct the sys_config table.

Regards
Ian Dobson

---

### Post by ian dobson on 2020-11-29
ended up reinstalling mysql, which is a pain as I had to reinstall mythtv.

regards
Ian Dobson

---

