---
title: "Can not install mysql-client and mysql-server on ubuntu 16.04"
date: 2016-05-19
forum: Installation &amp; Upgrades
---

### Post by roya2 on 2016-05-19
Hi, I have just installed ubuntu 16.04 and I needed to install mysql. 
I first did the update and upgrade and then :
```
sudo apt-get --yes install mysql-client mysql-server 
```

The last part that may show the error while installing is as follows:
```
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libhtml-template-perl (2.95-2) ...
Setting up mysql-client (5.7.12-0ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                         dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for systemd (229-4ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by roya2 on 2016-05-25
post #16 in [this thread]("http://ubuntuforums.org/showthread.php?t=1763604&page=2") solved my problem.

---

