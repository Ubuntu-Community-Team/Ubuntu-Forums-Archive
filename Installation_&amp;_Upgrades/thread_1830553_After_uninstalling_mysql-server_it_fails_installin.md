---
title: "After uninstalling mysql-server it fails installing it again"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by ZequeZ on 2011-08-21
So I messed up the mysql installation and I decided to reinstall it.

```

sudo apt-get purge mysql-server*
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
dpkg --configure -a
sudo rm -rf /var/lib/mysql /var/log/mysql /etc/mysql

```

So I do:

```

sudo apt-get install mysql-server
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  mysql-server-5.1 mysql-server-core-5.1
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.1 mysql-server-core-5.1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.9 MB of archives.
After this operation, 25.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? Get:1 http://ar.archive.ubuntu.com/ubuntu/ natty/main mysql-server-core-5.1 i386 5.1.54-1ubuntu4 [4,627 kB]
Get:2 http://ar.archive.ubuntu.com/ubuntu/ natty/main mysql-server-5.1 i386 5.1.54-1ubuntu4 [6,258 kB]
Get:3 http://ar.archive.ubuntu.com/ubuntu/ natty/main mysql-server all 5.1.54-1ubuntu4 [6,828 B]
Preconfiguring packages ...

[I think here comes the password screen]

Fetched 10.9 MB in 1min 30s (120 kB/s)
Selecting previously deselected package mysql-server-core-5.1.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 78188 files and directories currently installed.)
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.54-1ubuntu4_i386.deb) ...
Selecting previously deselected package mysql-server-5.1.
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.54-1ubuntu4_i386.deb) ...
egrep: /etc/mysql/: No such file or directory
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.54-1ubuntu4_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up mysql-server-core-5.1 (5.1.54-1ubuntu4) ...

```

After a few lines of output it asks me for the password for the root user...

But then it starts setting up mysql-server-5.1

```


Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
110821 23:00:48 [Note] Plugin 'FEDERATED' is disabled.
110821 23:00:48  InnoDB: Initializing buffer pool, size = 8.0M
110821 23:00:48  InnoDB: Completed initialization of buffer pool
110821 23:00:48  InnoDB: Started; log sequence number 0 44233
110821 23:00:48  InnoDB: Starting shutdown...
110821 23:00:53  InnoDB: Shutdown completed; log sequence number 0 44233
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.1
 mysql-server

```

And it fail.

The ouput of the syslog is this:

```


Aug 21 23:00:42 ubuntu mysqld[23389]: 
Aug 21 23:00:42 ubuntu mysqld[23389]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Aug 21 23:00:42 ubuntu mysqld[23389]: To do so, start the server, then issue the following commands:
Aug 21 23:00:42 ubuntu mysqld[23389]: 
Aug 21 23:00:42 ubuntu mysqld[23389]: /usr/bin/mysqladmin -u root password 'new-password'
Aug 21 23:00:42 ubuntu mysqld[23389]: /usr/bin/mysqladmin -u root -h ubuntu password 'new-password'
Aug 21 23:00:42 ubuntu mysqld[23389]: 
Aug 21 23:00:42 ubuntu mysqld[23389]: Alternatively you can run:
Aug 21 23:00:42 ubuntu mysqld[23389]: /usr/bin/mysql_secure_installation
Aug 21 23:00:42 ubuntu mysqld[23389]: 
Aug 21 23:00:42 ubuntu mysqld[23389]: which will also give you the option of removing the test
Aug 21 23:00:42 ubuntu mysqld[23389]: databases and anonymous user created by default.  This is
Aug 21 23:00:42 ubuntu mysqld[23389]: strongly recommended for production servers.
Aug 21 23:00:42 ubuntu mysqld[23389]: 
Aug 21 23:00:42 ubuntu mysqld[23389]: See the manual for more instructions.
Aug 21 23:00:42 ubuntu mysqld[23389]: 
Aug 21 23:00:42 ubuntu mysqld[23389]: Please report any problems with the /usr/bin/mysqlbug script!
Aug 21 23:00:42 ubuntu mysqld[23389]: 
Aug 21 23:00:42 ubuntu mysqld[23420]: 110821 23:00:42 [Note] Plugin 'FEDERATED' is disabled.
Aug 21 23:00:42 ubuntu mysqld[23420]: 110821 23:00:42  InnoDB: Initializing buffer pool, size = 8.0M
Aug 21 23:00:42 ubuntu mysqld[23420]: 110821 23:00:42  InnoDB: Completed initialization of buffer pool
Aug 21 23:00:42 ubuntu mysqld[23420]: InnoDB: The first specified data file ./ibdata1 did not exist:
Aug 21 23:00:42 ubuntu mysqld[23420]: InnoDB: a new database to be created!
Aug 21 23:00:42 ubuntu mysqld[23420]: 110821 23:00:42  InnoDB: Setting file ./ibdata1 size to 10 MB
Aug 21 23:00:42 ubuntu mysqld[23420]: InnoDB: Database physically writes the file full: wait...
Aug 21 23:00:42 ubuntu mysqld[23420]: 110821 23:00:42  InnoDB: Log file ./ib_logfile0 did not exist: new to be created
Aug 21 23:00:42 ubuntu mysqld[23420]: InnoDB: Setting log file ./ib_logfile0 size to 5 MB
Aug 21 23:00:42 ubuntu mysqld[23420]: InnoDB: Database physically writes the file full: wait...
Aug 21 23:00:42 ubuntu mysqld[23420]: 110821 23:00:42  InnoDB: Log file ./ib_logfile1 did not exist: new to be created
Aug 21 23:00:42 ubuntu mysqld[23420]: InnoDB: Setting log file ./ib_logfile1 size to 5 MB
Aug 21 23:00:42 ubuntu mysqld[23420]: InnoDB: Database physically writes the file full: wait...
Aug 21 23:00:43 ubuntu mysqld[23420]: InnoDB: Doublewrite buffer not found: creating new
Aug 21 23:00:43 ubuntu mysqld[23420]: InnoDB: Doublewrite buffer created
Aug 21 23:00:43 ubuntu mysqld[23420]: InnoDB: Creating foreign key constraint system tables
Aug 21 23:00:43 ubuntu mysqld[23420]: InnoDB: Foreign key constraint system tables created
Aug 21 23:00:43 ubuntu mysqld[23420]: 110821 23:00:43  InnoDB: Started; log sequence number 0 0
Aug 21 23:00:43 ubuntu mysqld[23420]: 110821 23:00:43  InnoDB: Starting shutdown...
Aug 21 23:00:48 ubuntu mysqld[23420]: 110821 23:00:48  InnoDB: Shutdown completed; log sequence number 0 44233
Aug 21 23:00:53 ubuntu mysqld[23451]: 110821 23:00:53 [Note] Plugin 'FEDERATED' is disabled.
Aug 21 23:00:53 ubuntu mysqld[23451]: 110821 23:00:53  InnoDB: Initializing buffer pool, size = 8.0M
Aug 21 23:00:53 ubuntu mysqld[23451]: 110821 23:00:53  InnoDB: Completed initialization of buffer pool
Aug 21 23:00:53 ubuntu mysqld[23451]: 110821 23:00:53  InnoDB: Started; log sequence number 0 44233
Aug 21 23:00:53 ubuntu mysqld[23451]: ERROR: 1064  You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ALTER TABLE user ADD column Show_view_priv enum('N','Y') CHARACTER SET utf8 NOT ' at line 1
Aug 21 23:00:53 ubuntu mysqld[23451]: 110821 23:00:53 [ERROR] Aborting
Aug 21 23:00:53 ubuntu mysqld[23451]: 
Aug 21 23:00:53 ubuntu mysqld[23451]: 110821 23:00:53  InnoDB: Starting shutdown...
Aug 21 23:00:59 ubuntu mysqld[23451]: 110821 23:00:59  InnoDB: Shutdown completed; log sequence number 0 44233
Aug 21 23:00:59 ubuntu mysqld[23451]: 110821 23:00:59 [Note] /usr/sbin/mysqld: Shutdown complete
Aug 21 23:00:59 ubuntu mysqld[23451]: 
Aug 21 23:00:59 ubuntu mysqld[23466]: 110821 23:00:59 [Note] Plugin 'FEDERATED' is disabled.
Aug 21 23:00:59 ubuntu mysqld[23466]: 110821 23:00:59  InnoDB: Initializing buffer pool, size = 8.0M
Aug 21 23:00:59 ubuntu mysqld[23466]: 110821 23:00:59  InnoDB: Completed initialization of buffer pool
Aug 21 23:00:59 ubuntu mysqld[23466]: 110821 23:00:59  InnoDB: Started; log sequence number 0 44233
Aug 21 23:00:59 ubuntu mysqld[23466]: 110821 23:00:59  InnoDB: Starting shutdown...
Aug 21 23:01:04 ubuntu mysqld[23466]: 110821 23:01:04  InnoDB: Shutdown completed; log sequence number 0 44233
Aug 21 23:01:04 ubuntu mysqld[23481]: 110821 23:01:04 [Note] Plugin 'FEDERATED' is disabled.
Aug 21 23:01:04 ubuntu mysqld[23481]: 110821 23:01:04  InnoDB: Initializing buffer pool, size = 8.0M
Aug 21 23:01:04 ubuntu mysqld[23481]: 110821 23:01:04  InnoDB: Completed initialization of buffer pool
Aug 21 23:01:04 ubuntu mysqld[23481]: 110821 23:01:04  InnoDB: Started; log sequence number 0 44233
Aug 21 23:01:04 ubuntu mysqld[23481]: ERROR: 1050  Table 'plugin' already exists
Aug 21 23:01:04 ubuntu mysqld[23481]: 110821 23:01:04 [ERROR] Aborting
Aug 21 23:01:04 ubuntu mysqld[23481]: 
Aug 21 23:01:04 ubuntu mysqld[23481]: 110821 23:01:04  InnoDB: Starting shutdown...
Aug 21 23:01:09 ubuntu mysqld[23481]: 110821 23:01:09  InnoDB: Shutdown completed; log sequence number 0 44233
Aug 21 23:01:09 ubuntu mysqld[23481]: 110821 23:01:09 [Note] /usr/sbin/mysqld: Shutdown complete
Aug 21 23:01:09 ubuntu mysqld[23481]: 
Aug 21 23:01:10 ubuntu init: mysql pre-start process (23523) terminated with status 1

```

There is no outout on any mysql log file.

And the dpkg.log have this:

```


2011-08-21 23:00:34 startup archives unpack
2011-08-21 23:00:34 install mysql-server-core-5.1 <none> 5.1.54-1ubuntu4
2011-08-21 23:00:34 status half-installed mysql-server-core-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:35 status triggers-pending man-db 2.5.9-4
2011-08-21 23:00:35 status half-installed mysql-server-core-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:36 status unpacked mysql-server-core-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:36 status unpacked mysql-server-core-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:36 install mysql-server-5.1 <none> 5.1.54-1ubuntu4
2011-08-21 23:00:36 status half-installed mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:37 status triggers-pending ureadahead 0.100.0-11
2011-08-21 23:00:37 status half-installed mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:37 status triggers-pending ureadahead 0.100.0-11
2011-08-21 23:00:38 status half-installed mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:39 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:39 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:39 install mysql-server <none> 5.1.54-1ubuntu4
2011-08-21 23:00:39 status half-installed mysql-server 5.1.54-1ubuntu4
2011-08-21 23:00:39 status unpacked mysql-server 5.1.54-1ubuntu4
2011-08-21 23:00:39 status unpacked mysql-server 5.1.54-1ubuntu4
2011-08-21 23:00:39 trigproc man-db 2.5.9-4 2.5.9-4
2011-08-21 23:00:39 status half-configured man-db 2.5.9-4
2011-08-21 23:00:40 status installed man-db 2.5.9-4
2011-08-21 23:00:40 trigproc ureadahead 0.100.0-11 0.100.0-11
2011-08-21 23:00:40 status half-configured ureadahead 0.100.0-11
2011-08-21 23:00:40 status installed ureadahead 0.100.0-11
2011-08-21 23:00:40 startup packages configure
2011-08-21 23:00:40 configure mysql-server-core-5.1 5.1.54-1ubuntu4 <none>
2011-08-21 23:00:40 status unpacked mysql-server-core-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status half-configured mysql-server-core-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status installed mysql-server-core-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 configure mysql-server-5.1 5.1.54-1ubuntu4 <none>
2011-08-21 23:00:40 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status unpacked mysql-server-5.1 5.1.54-1ubuntu4
2011-08-21 23:00:40 status half-configured mysql-server-5.1 5.1.54-1ubuntu4

```


I been with this the whole day, I'm running out of ideas and keywords in Google.

Also after I TRY to install mysql-server, everytime I use apt-get  it tries to

```
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
```

And it fails with the same error, even when I try to install something totally unrelated to mysql. And the only way I can solve this is with apt-get remove/purge mysql-server*

Why mysql hates me?

---

