---
title: "Trying to install mysql but a past install is haunting me"
date: 2019-04-10
forum: Installation &amp; Upgrades
---

### Post by filifunk on 2019-04-10
```


sudo apt install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server-5.7
  mysql-server-core-5.7
Suggested packages:
  mailx tinyca
The following NEW packages will be installed:
  mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server
  mysql-server-5.7 mysql-server-core-5.7
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/20.3 MB of archives.
After this operation, 160 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
(Reading database ... 254084 files and directories currently installed.)
Preparing to unpack .../mysql-common_5.8+1.0.4_all.deb ...
Unpacking mysql-common (5.8+1.0.4) ...
Selecting previously unselected package mysql-client-core-5.7.
Preparing to unpack .../mysql-client-core-5.7_5.7.25-0ubuntu0.18.04.2_amd64.deb ...
Unpacking mysql-client-core-5.7 (5.7.25-0ubuntu0.18.04.2) ...
Selecting previously unselected package mysql-client-5.7.
Preparing to unpack .../mysql-client-5.7_5.7.25-0ubuntu0.18.04.2_amd64.deb ...
Unpacking mysql-client-5.7 (5.7.25-0ubuntu0.18.04.2) ...
Selecting previously unselected package mysql-server-core-5.7.
Preparing to unpack .../mysql-server-core-5.7_5.7.25-0ubuntu0.18.04.2_amd64.deb ...
Unpacking mysql-server-core-5.7 (5.7.25-0ubuntu0.18.04.2) ...
Setting up mysql-common (5.8+1.0.4) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Selecting previously unselected package mysql-server-5.7.
(Reading database ... 254240 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.25-0ubuntu0.18.04.2_amd64.deb ...
Unpacking mysql-server-5.7 (5.7.25-0ubuntu0.18.04.2) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.7.25-0ubuntu0.18.04.2_all.deb ...
Unpacking mysql-server (5.7.25-0ubuntu0.18.04.2) ...
Processing triggers for ureadahead (0.100.0-20) ...
Setting up mysql-server-core-5.7 (5.7.25-0ubuntu0.18.04.2) ...
Processing triggers for systemd (237-3ubuntu10.19) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Setting up mysql-client-core-5.7 (5.7.25-0ubuntu0.18.04.2) ...
Setting up mysql-client-5.7 (5.7.25-0ubuntu0.18.04.2) ...
Setting up mysql-server-5.7 (5.7.25-0ubuntu0.18.04.2) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Renaming removed key_buffer and myisam-recover options (if present)
dpkg: error processing package mysql-server-5.7 (--configure):
 installed mysql-server-5.7 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for systemd (237-3ubuntu10.19) ...
Processing triggers for ureadahead (0.100.0-20) ...
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I have purged every mysql package that shows up using dpkg -l | grep mysql  before installing.  I don't know what to do.

I have ubuntu 18.04

---

