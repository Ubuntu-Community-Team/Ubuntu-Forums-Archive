---
title: "Upgrade to 10.04 causes MySQL headaches"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by dgavenda on 2010-05-26
After upgrading to 10.04 on a server, MySQL does not start.  I have tried multiple things from posts.  Nothing has worked.  

So, I down to reinstalling MySQL.  That doesn't even work.  It freezes w/ the following log:


Setting up libdbd-mysql-perl (4.012-1ubuntu1) ...
Setting up mysql-client-core-5.1 (5.1.41-3ubuntu12.1) ...
Setting up mysql-client-5.1 (5.1.41-3ubuntu12.1) ...
Setting up mysql-server-core-5.1 (5.1.41-3ubuntu12.1) ...
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.1) ...
100526 10:41:12 [Note] Plugin 'FEDERATED' is disabled.
100526 10:41:12  InnoDB: Started; log sequence number 0 44233
100526 10:41:12 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
ERROR: 1017  Can't find file: './mysql/user.frm' (errno: 13)
100526 10:41:12 [ERROR] Aborting

100526 10:41:12  InnoDB: Starting shutdown...
100526 10:41:13  InnoDB: Shutdown completed; log sequence number 0 44233
100526 10:41:13 [Note] /usr/sbin/mysqld: Shutdown complete



Most of my hair has already been pulled out so any help would be greatly appreciated.  If you want to see any logs, please let me know.  Ya, I am at my wits end.


Here's some more logging:
invoke-rc.d: initscript apparmor, action "start" failed.
 * Reloading AppArmor profiles                                                                                                                   
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
AppArmor parser error in /etc/apparmor.d/usr.sbin.mysqld at line 399: Could not open '(null)'
Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode
                                                                                                                                          [fail]

---

### Post by nunrgguy on 2010-11-15
I've got this. Did you get any joy?

---

