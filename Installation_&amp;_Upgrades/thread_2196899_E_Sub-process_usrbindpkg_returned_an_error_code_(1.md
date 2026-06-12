---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-01-01
forum: Installation &amp; Upgrades
---

### Post by kann.27 on 2014-01-01
root@qwe:~# sudo apt-get install mysql-server php5-mysql
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmariadbclient18 libmysqlclient18 mariadb-common
  mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server-5.5
  mysql-server-core-5.5
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libmariadbclient18 libmysqlclient18 mariadb-common
  mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server
  mysql-server-5.5 mysql-server-core-5.5 php5-mysql
0 upgraded, 11 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/26.3 MB of archives.
After this operation, 95.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
(Reading database ... 60545 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_10.0.7+maria-1~precise_all.deb) ...
Selecting previously unselected package mariadb-common.
Unpacking mariadb-common (from .../mariadb-common_10.0.7+maria-1~precise_all.deb) ...
Selecting previously unselected package libmariadbclient18.
Unpacking libmariadbclient18 (from .../libmariadbclient18_10.0.7+maria-1~precise_amd64.deb) ...
Selecting previously unselected package libmysqlclient18.
Unpacking libmysqlclient18 (from .../libmysqlclient18_10.0.7+maria-1~precise_amd64.deb) ...
Selecting previously unselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.020-1build2_amd64.deb) ...
Selecting previously unselected package mysql-client-core-5.5.
Unpacking mysql-client-core-5.5 (from .../mysql-client-core-5.5_5.5.34-0ubuntu0.12.04.1_amd64.deb) ...
Selecting previously unselected package mysql-client-5.5.
Unpacking mysql-client-5.5 (from .../mysql-client-5.5_5.5.34-0ubuntu0.12.04.1_amd64.deb) ...
Selecting previously unselected package mysql-server-core-5.5.
Unpacking mysql-server-core-5.5 (from .../mysql-server-core-5.5_5.5.34-0ubuntu0.12.04.1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mysql-common (10.0.7+maria-1~precise) ...
Selecting previously unselected package mysql-server-5.5.
(Reading database ... 60743 files and directories currently installed.)
Unpacking mysql-server-5.5 (from .../mysql-server-5.5_5.5.34-0ubuntu0.12.04.1_amd64.deb) ...
Selecting previously unselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.5.34-0ubuntu0.12.04.1_all.deb) ...
Selecting previously unselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.3.10-1ubuntu3.9_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up mariadb-common (10.0.7+maria-1~precise) ...
Setting up mysql-client-core-5.5 (5.5.34-0ubuntu0.12.04.1) ...
Setting up mysql-server-core-5.5 (5.5.34-0ubuntu0.12.04.1) ...
Setting up libmysqlclient18 (10.0.7+maria-1~precise) ...
Setting up libdbd-mysql-perl (4.020-1build2) ...
Setting up mysql-client-5.5 (5.5.34-0ubuntu0.12.04.1) ...
Setting up mysql-server-5.5 (5.5.34-0ubuntu0.12.04.1) ...
140101  7:01:50 [Warning] Using unique option prefix myisam_recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
140101  7:01:50 [Note] Plugin 'FEDERATED' is disabled.
140101  7:01:50 InnoDB: The InnoDB memory heap is disabled
140101  7:01:50 InnoDB: Mutexes and rw_locks use GCC atomic builtins
140101  7:01:50 InnoDB: Compressed tables use zlib 1.2.3.4
140101  7:01:50 InnoDB: Initializing buffer pool, size = 256.0M
InnoDB: mmap(274726912 bytes) failed; errno 12
140101  7:01:50 InnoDB: Completed initialization of buffer pool
140101  7:01:50 InnoDB: Fatal error: cannot allocate memory for the buffer pool
140101  7:01:50 [ERROR] Plugin 'InnoDB' init function returned error.
140101  7:01:50 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
140101  7:01:50 [ERROR] /usr/sbin/mysqld: unknown variable 'log_slow_verbosity=query_plan'
140101  7:01:50 [ERROR] Aborting

140101  7:01:50 [Note] /usr/sbin/mysqld: Shutdown complete

start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Setting up php5-mysql (5.3.10-1ubuntu3.9) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up libmariadbclient18 (10.0.7+maria-1~precise) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

