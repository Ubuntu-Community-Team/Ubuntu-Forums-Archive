---
title: "can't install mysql after hardy upgrade"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by piusvelte on 2008-04-28
This started off with a problem starting mysql, which was installed and functional on gutsy, but not since the hardy upgrade. I uninstalled mysql-server, and tried to reinstall, but I keep getting the following...

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
Reloading AppArmor profiles Warning: found /etc/apparmor.d/force-complain/usr.sbin.mysqld, forcing complain mode
: done.
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can't seem to install mysql-server at all. I thought this may have been an issue with apparmor, but from what I've read, complaint mode should be ok. When I uninstalled, I simply ran 'apt-get remove mysql-server'. That ran without any problems. Do I need to add purge or something else? Thank you!

---

### Post by piusvelte on 2008-04-28
I just ran apt-get remove --purge mysql-server, then apt-get autoremove to cleanup the dependencies, mysql-server-5.0, etc. I removed /var/run/mysql and /etc/mysql, though I have them backed up elsewhere. I tried reinstalling and am getting the same errors.

---

### Post by yyyc186 on 2008-05-01
The only solution I have found with Hardy is a complete wipe and re-install.  Plan on saving next to nothing.  This is definitely NOT an upgrade.

---

### Post by piusvelte on 2008-05-16
I've resolved most of my issues with hardy since upgrading, and am now turning back to mysql. I've run:
```

sudo apt-get remove --purge mysql-server
sudo apt-get remove --purge mysql-server-5.0

```
Then when trying to reinstall, I get prompted for the root password, and afterwards the installation fails configuring mysql-server-5.0. Is there a way to run the install in debug mode, or a log file somewhere that I could check for the specific issue?

I'm wondering if this has to do with the mysql user that mysql runs under. I went into users and groups and didn't see mysql anywhere. I believe that there's a rule in apparmor for it though. Perhaps there's still something left over from mysql that is causing the installation problem. I've moved the db files into a backup folder in my home directory. Where else can I check to purge mysql reminants? How can I re-initialize apparmor to avoid any lingering mysql configuration there? Should I re-install apparmor?

Thanks!

---

### Post by tessmonsta on 2008-05-24
I'm having the same problem, any luck on fixing it?

---

### Post by auskento on 2008-05-26
I too am having the same problem, and a reinstall is out of the question.  I'd lose too much data from my LVM for this to be feasible.

I deleted every mysql folder I could find after purging mysql-server and mysql-server-5.0

Now it cannot even recreate the base mysql data file
```

$ mysql_install_db
Installing MySQL system tables...
ERROR: 1  Can't create/write to file '/var/lib/mysql/mysql/db.MYI' (Errcode: 13)
080527  9:20:02 [ERROR] Aborting

080527  9:20:02 [Note] /usr/sbin/mysqld: Shutdown complete

Installation of system tables failed!

```

Beginning to wish I hadn't dived into Hardy when i was assembling my new server.

---

