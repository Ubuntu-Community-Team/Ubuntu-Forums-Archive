---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by kaio123 on 2012-02-17
Guys i messed up trying to reinstall mythtv. somewhere i must have deleted mysql. Now when i try to reinstall or install i get this error. i searched and tried all these commands to no help

apt-get update
apt-get -f install mysql-server-5.1
apt-get clean
sudo apt-get remove --purge

Can anyone help ?

=================================
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
mysql-server depends on mysql-server-5.1; however:
Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
mythtv depends on mysql-server; however:
Package mysql-server is not configured yet.
Package mysql-server-5.1 which provides mysql-server is not configured yet.
dpkg: error processing mythtv (--configure):
dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
mysql-server-5.1
mysql-server
mythtv

---

### Post by cortman on 2012-02-17
Try running

```
sudo apt-get install -f
```

Note no package name included. Just running that should fix the filesystem. If not, post any error messages.

---

### Post by kaio123 on 2012-02-17
cortman thanks for the reply. tried your command but no luck. here's the output

kaio@ubuntuhtpc:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libpng12-0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.58-1ubuntu1) ...
120217 19:31:12 [Note] Plugin 'FEDERATED' is disabled.
120217 19:31:12  InnoDB: Initializing buffer pool, size = 8.0M
120217 19:31:12  InnoDB: Completed initialization of buffer pool
120217 19:31:12  InnoDB: Started; log sequence number 0 44233
120217 19:31:12  InnoDB: Starting shutdown...
120217 19:31:18  InnoDB: Shutdown completed; log sequence number 0 44233
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mysql-server; however:
  Package mysql-server is not configured yet.
  Package mysql-server-5.1 which provides mysql-server is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
               No apport report written because the error message indicates its a followup error from a previous failure.
                              Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cortman on 2012-02-17
Are you able to run

```
sudo apt-get purge mysql-server
sudo apt-get install mysql-server
```

successfully?

---

