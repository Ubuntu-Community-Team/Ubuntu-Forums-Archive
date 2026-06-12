---
title: "problem with uninstalling and reinstalling Postgresql"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by newbiepk on 2011-05-02
I'm a Linux newbie here. I'm using Ubuntu 10.10 on a Virtual Machine, and had previously installed Postgresql 8.4 then 9.0 on my VM, but later found out that there's a problem with my Postgres. My goal is to reinstall PG 9.0 properly on my VM.

I'd tried to remove the existing PG before reinstalling, by following some of the threads I found on this forum (and several others), which included:
$ sudo apt-get remove --purge postgresql
$ sudo add-apt-repository ppa:pitti/postgresql
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install -f
[...repeated the last 2 several times, per one of the threads I read...]
$ sudo apt-get autoremove

But I still got errors along the way, which I listed at the bottom here. Could anyone help me with this issue? Thanks!

=====================================================

### REMOVE ERRORS:
Reading package lists...
Building dependency tree...
Reading state information...
Package postgresql is not installed, so not removed
The following packages were automatically installed and are no longer required:
  postgresql-8.4 linux-headers-2.6.35-22-generic postgresql-client-8.4
  linux-headers-2.6.35-22 libossp-uuid16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-9.0 (9.0.4-1~maverick1) ...
 * Starting PostgreSQL 9.0 database server       [167G  [31m*[39;49m Error: /var/lib/postgresql/9.0/main is not accessible or does not exist

[161G[[31mfail[39;49m]
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-9.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-9.0
E: Sub-process /usr/bin/dpkg returned an error code (1)


### UPDATE is OK

### UPGRADE ERROR

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Setting up postgresql-9.0 (9.0.4-1~maverick1) ...
 * Starting PostgreSQL 9.0 database server       [167G  [31m*[39;49m Error: /var/lib/postgresql/9.0/main is not accessible or does not exist

[161G[[31mfail[39;49m]
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-9.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-9.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

### INSTALL -F ERROR

Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  postgresql-8.4 linux-headers-2.6.35-22-generic postgresql-client-8.4
  linux-headers-2.6.35-22 libossp-uuid16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-9.0 (9.0.4-1~maverick1) ...
 * Starting PostgreSQL 9.0 database server       [80G  [31m*[39;49m Error: /var/lib/postgresql/9.0/main is not accessible or does not exist

[74G[[31mfail[39;49m]
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-9.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-9.0
E: Sub-process /usr/bin/dpkg returned an error code (1)


### AUTOREMOVE ERROR
cc2@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libossp-uuid16 linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
  postgresql-8.4 postgresql-client-8.4
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 103MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 151365 files and directories currently installed.)
Removing libossp-uuid16 ...
Removing linux-headers-2.6.35-22-generic ...
Removing linux-headers-2.6.35-22 ...
Removing postgresql-8.4 ...
 * Stopping PostgreSQL 8.4 database server                                       * Error: /var/lib/postgresql/8.4/main is not accessible or does not exist
                                                                         [fail]
invoke-rc.d: initscript postgresql, action "stop" failed.
dpkg: error processing postgresql-8.4 (--remove):
 subprocess installed pre-removal script returned error exit status 1
dpkg: postgresql-client-8.4: dependency problems, but removing anyway as you requested:
 postgresql-8.4 depends on postgresql-client-8.4.
Removing postgresql-client-8.4 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postgresql-8.4
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

