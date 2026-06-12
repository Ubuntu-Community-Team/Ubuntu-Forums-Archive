---
title: "MYSQL server not working."
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by Ketan_Parihar on 2014-10-27
Hi,

I get below error when i try to start the mysql from my Ubuntu 14.04 machine. 

root@ketan:/home/ketanpar# mysqld start
Warning: World-writable config file '/etc/mysql/my.cnf' is ignored
2014-10-27 14:10:56 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2014-10-27 14:10:56 6864 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!


2014-10-27 14:10:56 6864 [ERROR] Aborting


2014-10-27 14:10:56 6864 [Note] Binlog end
2014-10-27 14:10:56 6864 [Note] mysqld: Shutdown complete

Please help me start mysql server on my system.

---

### Post by nerdtron on 2014-10-27
```
Warning: World-writable config file '/etc/mysql/my.cnf' is ignored
```

Did you do a chmod or chown command on your /etc/mysql/my.cnf file?

You should revert it back to default:
```
sudo chmod 644 /etc/mysql/my.cnf 
ls -lh /etc/mysql/my.cnf
```

---

