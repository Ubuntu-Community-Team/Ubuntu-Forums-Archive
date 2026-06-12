---
title: "Mysql doesn't work after gutsy upgrade"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by allspiritseve on 2007-10-26
I have successfully upgraded to gutsy.. however my mysql does not function anymore.

I have received this error:
```
Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas? I didn't really have any databases in there I can't replace, so if reinstallation is necessary, that is no problem.

Thanks,

Cory

---

### Post by ffteixeira on 2008-02-26
Make only this change in my.cnf file:

**sudo /etc/mysql/my.cnf**

change line: **bind-address            = 127.0.0.1** 

to:               : **bind-address            = 0.0.0.0**

Form me work well

---

