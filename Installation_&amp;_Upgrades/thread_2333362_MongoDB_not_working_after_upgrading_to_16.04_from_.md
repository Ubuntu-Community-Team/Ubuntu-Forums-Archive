---
title: "MongoDB not working after upgrading to 16.04 from 14.04"
date: 2016-08-09
forum: Installation &amp; Upgrades
---

### Post by hamzatrq on 2016-08-09
Two days back I got a notification to upgrade to 16.04.2 which I did. But now MongoDB stopped working. So I reinstalled it, even than it didn't worked the problem was with some permissions. After which I uninstalled it completely even removing folders and ppas and everything that was related (followed an answer). Still got the same error. Now I have tried the third time. I have also tried changing the permissions of ```
/var/log/mongodb
``` ```
/var/lib/mongodb
``` to 755 and changing the port in ```
/etc/mongod.conf
```. I don't want to reinstall ubuntu and therefore need help.

The error I get when trying to run mongo shell.

```

$ mongo
MongoDB shell version: 3.2.8
connecting to: test
2016-08-09T22:08:48.475+0500 W NETWORK  [thread1] Failed to connect to 127.0.0.1:27017, reason: errno:111 Connection refused
2016-08-09T22:08:48.517+0500 E QUERY    [thread1] Error: couldn't connect to server 127.0.0.1:27017, connection attempt failed :
connect@src/mongo/shell/mongo.js:229:14
@(connect):1:6


exception: connect failed



```

---

