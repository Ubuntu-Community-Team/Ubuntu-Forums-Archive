---
title: "Why does this happen when i try to install mysql-server"
date: 2018-09-30
forum: Installation &amp; Upgrades
---

### Post by matthewtranmer on 2018-09-30
```
matthew@matthewserver:~$ sudo apt-get install mysql-server-5.7
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  mysql-client-5.7 mysql-common
Suggested packages:
  mailx tinyca
The following NEW packages will be installed:
  mysql-client-5.7 mysql-common mysql-server-5.7
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/5,513 kB of archives.
After this operation, 81.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
dpkg: warning: files list file for package 'mysql-server-core-5.7' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mysql-client-core-5.7' missing; assuming package has no files currently installed
(Reading database ... 124748 files and directories currently installed.)
Preparing to unpack .../mysql-common_5.8+1.0.4_all.deb ...
Unpacking mysql-common (5.8+1.0.4) ...
Selecting previously unselected package mysql-client-5.7.
Preparing to unpack .../mysql-client-5.7_5.7.23-0ubuntu0.18.04.1_amd64.deb ...
Unpacking mysql-client-5.7 (5.7.23-0ubuntu0.18.04.1) ...
Setting up mysql-common (5.8+1.0.4) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Selecting previously unselected package mysql-server-5.7.
dpkg: warning: files list file for package 'mysql-server-core-5.7' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mysql-client-core-5.7' missing; assuming package has no files currently installed
(Reading database ... 124791 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.23-0ubuntu0.18.04.1_amd64.deb ...
Unpacking mysql-server-5.7 (5.7.23-0ubuntu0.18.04.1) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for systemd (237-3ubuntu10.3) ...
Processing triggers for man-db (2.8.3-2) ...
Setting up mysql-client-5.7 (5.7.23-0ubuntu0.18.04.1) ...
Setting up mysql-server-5.7 (5.7.23-0ubuntu0.18.04.1) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Renaming removed key_buffer and myisam-recover options (if present)
ERROR: Unable to start MySQL server:
/var/lib/dpkg/info/mysql-server-5.7.postinst: line 102: mysqld: command not found
Please take a look at [https://wiki.debian.org/Teams/MySQL/FAQ](https://wiki.debian.org/Teams/MySQL/FAQ) for tips on fixing common upgrade issues.
Once the problem is resolved, run apt-get --fix-broken install to retry.
dpkg: error processing package mysql-server-5.7 (--configure): installed mysql-server-5.7 package post-installation script subprocess returned error exit status 127Processing triggers for ureadahead (0.100.0-20) ...Processing triggers for systemd (237-3ubuntu10.3) ...Errors were encountered while processing: mysql-server-5.7E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by notesetter on 2018-09-30
I'm getting a similar error and returned error code (1). In my case, it's a problem with mysql-common (--configure) and something about update-alternatives.

Watching this thread.

---

### Post by i7Fd-2sCB1 on 2018-09-30
Could the error message be related to this Answers page: 

[https://askubuntu.com/questions/935340/getting-error-as-mysql-command-not-found](https://askubuntu.com/questions/935340/getting-error-as-mysql-command-not-found)

????

---

