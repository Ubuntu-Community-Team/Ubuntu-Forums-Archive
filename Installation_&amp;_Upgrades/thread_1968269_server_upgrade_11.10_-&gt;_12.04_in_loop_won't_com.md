---
title: "server upgrade 11.10 -&gt; 12.04 in loop won't complete"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by rgeddes on 2012-04-28
Hi,

I've upgraded two desktops from 11.10 to 12.04 without issues.

On upgrading a server, the install screen has been stuck for about 1 hour on this line:
```
Installing new version of config file /etc/apparmor.d/usr.sbin.mysqld ...
```
and /var/log/syslog keeps repeating the following lines:
```
Apr 28 22:24:44 spitfire kernel: [252317.450526] init: mysql main process (27743) terminated with status 1
Apr 28 22:24:44 spitfire kernel: [252317.450735] init: mysql main process ended, respawning
Apr 28 22:24:45 spitfire kernel: [252318.472315] init: mysql post-start process (27744) terminated with status 1
Apr 28 22:24:45 spitfire kernel: [252318.547191] type=1400 audit(1335666285.143:2571): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=27798 comm="apparmor_parser"
Apr 28 22:24:47 spitfire kernel: [252320.849578] init: mysql main process (27802) terminated with status 1
Apr 28 22:24:47 spitfire kernel: [252320.849783] init: mysql main process ended, respawning
Apr 28 22:24:48 spitfire kernel: [252321.868463] init: mysql post-start process (27803) terminated with status 1
Apr 28 22:24:48 spitfire kernel: [252321.943500] type=1400 audit(1335666288.539:2572): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=27857 comm="apparmor_parser"
```
I'm performing the upgrade over ssh and using screen to be able to detach if need be... hopefully, this isn't affecting the install.


How can I recover from this upgrade loop?

Thanks
R

RESOLVED:
mysql-proxy was installed, and somehow put the upgrade program in a loop.  Stopped mysql-proxy:
```
sudo servicemysql-proxy stop
```
and the upgrade program continued until completion

yay!

---

