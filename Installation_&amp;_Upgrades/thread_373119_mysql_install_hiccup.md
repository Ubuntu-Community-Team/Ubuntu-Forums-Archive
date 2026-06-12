---
title: "mysql install hiccup"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by djrobthaman on 2007-02-28
Hi,

I get the following output when I look at the details for synaptic while installing mysql-server-5.0

```

Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 121938 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.24a-9_amd64.deb) ...
Setting up mysql-server-5.0 (5.0.24a-9) ...
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.24a-9) ...
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0

```

Does anyone know how I could get this to install correctly?

Thanks,
Douglas

---

### Post by firefly2442 on 2007-02-28
Did you try updating the packages to make sure the dependencies were being met before hand?

> sudo apt-get update

I would also suggest a restart of the system and try it again.  Other than that I don't have any more ideas.  Maybe someone else has a suggestion. :)

---

### Post by djrobthaman on 2007-03-03
Hi,

Still haven't gotten it to work.  But I noticed that there are no files in the folder '/var/run/mysqld/'.  It seems that at least on e file by the name of mysqld.sock  should be in there.

Is there an easy way to just create the files that should be in there?  Or even a hard way?

Thanks,
Douglas

---

### Post by ecdolive on 2007-04-18
Did you ever get this resolved. I am currently having the same issue. I tried the uncommenting of "skip-innodb" in /etc/mysql/my.cnf and tried uninstalling and reinstalling over and over, but it always fails startup. It's driving me nuts.

---

### Post by djrobthaman on 2007-04-20
Actually I did.  Just uncommented skip-innodb in /etc/mysql/my.cnf (sorry).

---

### Post by brazzmonkey on 2007-04-21
well, i recently upgraded to feisty and i encounter similar issue. uncommenting skip-innodb didn't help, though.

---

### Post by brazzmonkey on 2007-04-21
actually i was getting incorrect file format errors on some system tables so mysql couldn't start (user table, for instance was affected). i tried this : [http://forums.mysql.com/read.php?10,119674,119723#msg-119723](http://forums.mysql.com/read.php?10,119674,119723#msg-119723) but couldn't repair the tables, so i backed up my personal tables, purged mysql-server-5.0 re-installed it and reconfigured it. Now it works.
still, i don't know if the upgrade to feisty is the culprit or if this is related to something else...

---

