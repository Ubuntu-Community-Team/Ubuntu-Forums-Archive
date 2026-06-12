---
title: "trying to overwrite '/usr/lib/libmysqlclient.so.16.0.0"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by bjarkith on 2010-05-22
I was trying to install some mysql tools on my lap when the installation of one of the tools froze and force quit, now I one of the tools seems to be stuck in update manager as a new install but it cant be installed or removed and when I use update manager I always get this error:

E: /var/cache/apt/archives/libmysqlclient16_5.1.41-3ubuntu12.1_i386.deb: trying to overwrite '/usr/lib/libmysqlclient.so.16.0.0', which is also in package mysql-cluster-client-5.1 0

Does anyone know how to fix this?

---

### Post by arrange on 2010-05-22
Hmm, they seem to be in conflict, have you tried uninstalling *libmysqlclient16*?

For example from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)```
sudo apt-get remove libmysqlclient16
```

or if that doesn't work```
sudo dpkg -r libmysqlclient16
```

If still no luck, post the output of the above commands + ```
sudo dpkg --configure -a
dpkg -l | grep mysql
```

---

### Post by bjarkith on 2010-05-22
The first command gave me this:

> kak@laptop:~$ sudo apt-get remove libmysqlclient16
[sudo] password for bjarki: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmysqlclient16 is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libmysqlclient-dev: Depends: libmysqlclient16 (= 5.1.41-3ubuntu12.1) but it is not going to be installed
  php5-mysql: Depends: libmysqlclient16 (>= 5.1.21-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
The second one gave me:

> kak@laptop:~$ sudo dpkg -r libmysqlclient16
dpkg: warning: ignoring request to remove libmysqlclient16 which isn't installed.
bjarki@bjarki-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libmysqlclient-dev:
 libmysqlclient-dev depends on libmysqlclient16 (= 5.1.41-3ubuntu12.1); however:
  Package libmysqlclient16 is not installed.
dpkg: error processing libmysqlclient-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-mysql:
 php5-mysql depends on libmysqlclient16 (>= 5.1.21-1); however:
  Package libmysqlclient16 is not installed.
dpkg: error processing php5-mysql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmysqlclient-dev
 php5-mysql
And the third gave me:

> kak@laptop:~$ dpkg -l | grep mysql
iU  libmysqlclient-dev                    5.1.41-3ubuntu12.1                              MySQL database development files
ii  mysql-cluster-client-5.1              7.0.9-1ubuntu7                                  MySQL database client binaries
ii  mysql-cluster-server                  7.0.9-1ubuntu7                                  MySQL database server (metapackage depending
ri  mysql-cluster-server-5.1              7.0.9-1ubuntu7                                  MySQL database server binaries
ii  mysql-common                          5.1.41-3ubuntu12.1                              MySQL database common files (e.g. /etc/mysql
iU  php5-mysql                            5.3.2-1ubuntu4.2                                MySQL module for php5
But didn't resolve the problem, it seems that the libmysqlclient16 isnt installed but it wont go out of installation queue in the update manager.

---

### Post by arrange on 2010-05-22
Well, the packages *libmysqlclient16* and *mysql-cluster-client-5.1* are clearly in conflict, as they both use their own files in */usr/lib/* of the same name (but different contents). You should use just one of the packages, but as I don't use *mysql*, I can't advice you on which one is more important :)

---

### Post by bjarkith on 2010-05-22
Well i'v tryed to reinstall, uninstall or just plain install all of these mysql packages but none of the functions correctly and its all due to that libmysqlclient16. It's getting wery frustrating.

---

### Post by bjarkith on 2010-05-23
I managed to fix it somehow, not rly shure what I did but it's ok now.

---

