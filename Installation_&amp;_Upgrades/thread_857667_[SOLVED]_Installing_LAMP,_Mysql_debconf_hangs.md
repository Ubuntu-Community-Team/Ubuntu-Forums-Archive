---
title: "[SOLVED] Installing LAMP, Mysql debconf hangs"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by Statik on 2008-07-12
Hi all,
New install of 8.04 on a HP DV2310CA. Did all updates. Got the wireless working, and all other hardware worked out of the box. So, my next thing, install LAMP. Tried the apt-get tasksel route and the Synaptic select-by-task method. Install always seems to hang with Mysql-server-5.0 install, after entering a root password. With synaptic, the debconf window goes dark and stops responding.

What can I do?

Statik

---

### Post by Statik on 2008-07-12
Decided to leave the debconf window up for a while. After 20mins it started up again. After responding to a question, another long wait, the another question, then wait. Finally:
```
E: mysql-server-5.0: subprocess post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured


```

and then long messages that I can't copy.

Statik

---

### Post by Statik on 2008-07-12
Tried apt-get install mtsql-server-5.0 and got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server-5.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles : done.
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

ideas?

Statik

---

### Post by Statik on 2008-07-13
Weirdly enough, I've solved this without trying. I had another problem with apache in that localhost wasn't responding. I researched it and saw on boot the message about it ignoring an unknown network lo=lo, as shown in this thread [http://ubuntuforums.org/showthread.php?t=858081]("http://ubuntuforums.org/showthread.php?t=858081")

When I fixed that problem, the Mysql install problem went away as well! LO works with apache and Mysql is installed!

Thanks to all!

Statik

---

