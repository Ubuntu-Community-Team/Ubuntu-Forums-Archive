---
title: "mysql update that came today"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by dazer26 on 2010-02-10
So there was a mysql update today and it dodn't finish and left me with an error.  I tried renaming my config file, re-installing mysql 5.1, all with no luck.  I'd like to avoid removing and re-installing as I would have to re-install myth-tv again.  Setting up mysql and myth-tv can take longer than installing the entire OS....I really with there was a simple TV program for my TV-card lol, as much as I love all the options in myth-tv, I don't use 99% of the features, I just wanna watch TV! /rant

Most people seem to have had this problem a year ago, or 4 months ago when upgrading to 9.10.  I did a fresh install of 9.10, so it was just the updates that came today that fudged things up.



Preconfiguring packages ...
(Reading database ... 297712 files and directories currently installed.)
Preparing to replace mysql-common 5.1.37-1ubuntu5 (using .../mysql-common_5.1.37-1ubuntu5.1_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace mysql-server 5.1.37-1ubuntu5 (using .../mysql-server_5.1.37-1ubuntu5.1_all.deb) ...
Unpacking replacement mysql-server ...
Preparing to replace mysql-client 5.1.37-1ubuntu5 (using .../mysql-client_5.1.37-1ubuntu5.1_all.deb) ...
Unpacking replacement mysql-client ...
Preparing to replace libmysqlclient16 5.1.37-1ubuntu5 (using .../libmysqlclient16_5.1.37-1ubuntu5.1_i386.deb) ...
Unpacking replacement libmysqlclient16 ...
Preparing to replace mysql-client-5.1 5.1.37-1ubuntu5 (using .../mysql-client-5.1_5.1.37-1ubuntu5.1_i386.deb) ...
Unpacking replacement mysql-client-5.1 ...
Preparing to replace mysql-server-core-5.1 5.1.37-1ubuntu5 (using .../mysql-server-core-5.1_5.1.37-1ubuntu5.1_i386.deb) ...
Unpacking replacement mysql-server-core-5.1 ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up mysql-common (5.1.37-1ubuntu5.1) ...
(Reading database ... 297712 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.37-1ubuntu5 (using .../mysql-server-5.1_5.1.37-1ubuntu5.1_i386.deb) ...
 * Stopping MySQL database server mysqld
   ...done.
 * Stopping MySQL database server mysqld
   ...done.
Unpacking replacement mysql-server-5.1 ...
Preparing to replace gnome-screensaver 2.28.0-0ubuntu3.3 (using .../gnome-screensaver_2.28.0-0ubuntu3.4_i386.deb) ...
Unpacking replacement gnome-screensaver ...
Preparing to replace kde-l10n-engb 4:4.3.5-0ubuntu1~karmic1 (using .../kde-l10n-engb_4%3a4.4.0-0ubuntu1~karmic1~ppa1_all.deb) ...
Unpacking replacement kde-l10n-engb ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up libmysqlclient16 (5.1.37-1ubuntu5.1) ...

Setting up mysql-client-5.1 (5.1.37-1ubuntu5.1) ...

Setting up mysql-server-core-5.1 (5.1.37-1ubuntu5.1) ...
Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Setting up mysql-client (5.1.37-1ubuntu5.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up gnome-screensaver (2.28.0-0ubuntu3.4) ...

Setting up kde-l10n-engb (4:4.4.0-0ubuntu1~karmic1~ppa1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...fail!
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

---

### Post by Wlo on 2010-02-11
Same problem here since attempting to install the update earlier today.

```

:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following partially installed packages will be configured:
  mysql-server mysql-server-5.1 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                                [ OK ] 
 * Starting MySQL database server mysqld                                                                                                                [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                                [ OK ] 
 * Starting MySQL database server mysqld                                                                                                                [fail] 
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
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

```

Seems that it can't start mysql to do some part of the update.

Wlo.

---

### Post by Wlo on 2010-02-11
Ah, I'm on Gnome/Ubunutu rather than Kubuntu btw - found this via a search.

---

### Post by Wlo on 2010-02-11
Have managed to fix this.

In my mysql log:

```

100211 21:33:22  InnoDB: Started; log sequence number 0 43795
/usr/sbin/mysqld: File './mysql-bin.000225' not found (Errcode: 13)
100211 21:33:22 [ERROR] Failed to open log (file './mysql-bin.000225', errno 13)
100211 21:33:22 [ERROR] Could not open log file
100211 21:33:22 [ERROR] Can't init tc log
100211 21:33:22 [ERROR] Aborting

```

I fixed this by disabling the bin log.

in /etc/mysql/my.cnf I commented out the following two lines (put a # at the beginning):

```

# log-bin=mysql-bin

```
```

# binlog_format=mixed

```

The server is now able to start okay, and consequently upgrade okay.

Prior to that I emptied the file /var/lib/mysql/mysql-bin.index.  I'm not sure if that was necessary or not, I suspect not, but try it if the above doesn't work by itself.

It's a worry that a mysql update by itself was able to prevent the server from starting.

Cheers.

Wlo.

---

### Post by snop on 2010-02-12
Hello,

Suffered the same problem with the MySQL upgrade. My solution was to kill the mysqld process before installing the update.

---

### Post by vahid4134 on 2010-02-14
I fix this problem with this way
read  /etc/mysql/debian.cnf and copy password for debian-sys-maint and set this password for debian-sys-maint mysql user

---

### Post by Temik on 2010-02-15
I fixed it this way.
I replaced my /etc/mysql/my.cnf with this one and mysql started immediately.


```
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket = /var/run/mysqld/mysqld.sock
port = 3306
basedir		= /usr
datadir = /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
myisam-recover		= BACKUP
query_cache_limit       = 1M
query_cache_size        = 16M
expire_logs_days	= 10
max_binlog_size         = 100M

#skip-bdb

skip-federated
big-tables

[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]


[isamchk]
key_buffer		= 16M
bind-address            =127.0.0.1
!includedir /etc/mysql/conf.d/
```

---

### Post by pettitti on 2010-02-16
> **snop said:**
> Hello,

Suffered the same problem with the MySQL upgrade. My solution was to kill the mysqld process before installing the update.

This was the only thing that worked for me

---

