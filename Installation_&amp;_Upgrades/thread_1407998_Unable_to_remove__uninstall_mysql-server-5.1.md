---
title: "Unable to remove / uninstall mysql-server-5.1"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by gcpitts on 2010-02-15
I've been trying to remove / uninstall mysql-server-5.1 for over a week now and I've had no success. At this point I don't even recall the initial issue that led me to resort to uninstalling it in the first place, but here's where I am.

The Synaptic Package Manager has notified me that Package **mysql-server-5.1 **is broken. So, I check the box for complete removal and receive this message:

**E: mysql-server-5.1: subprocess installed pre-removal script returned error exit status 2**

I've also attempted to remove it via the terminal by typing **sudo apt-get remove mysql-server-5.1** and I get this message:

[B]The following packages will be REMOVED:
  mysql-server-5.1
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
[/B]
Any help would be greatly appreciated.

---

### Post by Barriehie on 2010-02-15
Try:
```

apt-get purge mysql-server-5.1
```

---

### Post by gcpitts on 2010-02-16
Thanks for the suggestion. It didn't work, but I did manage to get it fixed--although, I have no idea how.

---

### Post by amites on 2010-05-13
I've been running into the same issue since upgrading

anyone come up with a work around - thinking my next step will be manual remove and re-install though would rather avoid that

situation in a nutshell

mysql service will not start

running sudo app-get remove mysql-server
  locks up the process
  same with --purge option

any ideas?

---

### Post by Gehaktbal on 2010-05-15
I am struggling with the same problems and it is really starting to **** me off. Pardon my language. But it interrupted with my dist-upgrade. A purge (complete deinstall?) or reinstall hangs the process on the stopping and starting of mysql.

Somebody please tell me how to manualy remove EVERY bit of mysql and to reset the upstart status of mysql and then to reinstall mysql from scratch?

---

### Post by rowinggolfer on 2010-05-15
here's what worked for me.

open 2 terminals.
in the first, execute

sudo apt-get remove mysql-server-5.1

when that hangs (because it perpetually loops callng mysqld stop... ) execute this is the 2nd terminal

sudo service mysql start


that seems to free the first terminal process.

---

### Post by Gehaktbal on 2010-05-15
Ok that indeed seemed to continue the purging of mysql. I reinstalled and it asked for root password etc. The install seemed to do pretty well and didn hang...BUT

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  libdbd-mysql-perl{a} libdbi-perl{a} libmysqlclient16{a} libnet-daemon-perl{a} libplrpc-perl{a} mysql-client-5.1{a} mysql-client-core-5.1{a} mysql-common{a} mysql-server 
  mysql-server-5.1{a} mysql-server-core-5.1{a} 
0 packages upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.2MB of archives. After unpacking 54.6MB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 170820 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.1.41-3ubuntu12_all.deb) ...
Selecting previously deselected package libnet-daemon-perl.
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.43-1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2020-2_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.609-1build1_i386.deb) ...
Selecting previously deselected package libmysqlclient16.
Unpacking libmysqlclient16 (from .../libmysqlclient16_5.1.41-3ubuntu12_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.012-1ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-client-core-5.1.
Unpacking mysql-client-core-5.1 (from .../mysql-client-core-5.1_5.1.41-3ubuntu12_i386.deb) ...
Selecting previously deselected package mysql-client-5.1.
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.41-3ubuntu12_i386.deb) ...
Selecting previously deselected package mysql-server-core-5.1.
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.41-3ubuntu12_i386.deb) ...
Processing triggers for man-db ...
Setting up mysql-common (5.1.41-3ubuntu12) ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 171183 files and directories currently installed.)
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.41-3ubuntu12_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.41-3ubuntu12_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up libnet-daemon-perl (0.43-1) ...
Setting up libplrpc-perl (0.2020-2) ...
Setting up libdbi-perl (1.609-1build1) ...
Setting up libmysqlclient16 (5.1.41-3ubuntu12) ...

Setting up libdbd-mysql-perl (4.012-1ubuntu1) ...
Setting up mysql-client-core-5.1 (5.1.41-3ubuntu12) ...
Setting up mysql-client-5.1 (5.1.41-3ubuntu12) ...
Setting up mysql-server-core-5.1 (5.1.41-3ubuntu12) ...
Setting up mysql-server-5.1 (5.1.41-3ubuntu12) ...
100516  1:47:21 [Note] Plugin 'FEDERATED' is disabled.
100516  1:47:21  InnoDB: Started; log sequence number 0 44233
100516  1:47:21  InnoDB: Starting shutdown...
100516  1:47:23  InnoDB: Shutdown completed; log sequence number 0 44233
start: Job is already running: mysql

Setting up mysql-server (5.1.41-3ubuntu12) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```

But after rebooting it still fails to start:
```
May 16 01:47:19 server kernel: [34497.865862] type=1503 audit(1273967239.884:64):  operation="capable" pid=21288 parent=21275 profile="/usr/sbin/mysqld" name="chown"
May 16 01:47:20 server mysqld[21276]: 
May 16 01:47:20 server mysqld[21276]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
May 16 01:47:20 server mysqld[21276]: To do so, start the server, then issue the following commands:
May 16 01:47:20 server mysqld[21276]: 
May 16 01:47:20 server mysqld[21276]: /usr/bin/mysqladmin -u root password 'new-password'
May 16 01:47:20 server mysqld[21276]: /usr/bin/mysqladmin -u root -h server password 'new-password'
May 16 01:47:20 server mysqld[21276]: 
May 16 01:47:20 server mysqld[21276]: Alternatively you can run:
May 16 01:47:20 server mysqld[21276]: /usr/bin/mysql_secure_installation
May 16 01:47:20 server mysqld[21276]: 
May 16 01:47:20 server mysqld[21276]: which will also give you the option of removing the test
May 16 01:47:20 server mysqld[21276]: databases and anonymous user created by default.  This is
May 16 01:47:20 server mysqld[21276]: strongly recommended for production servers.
May 16 01:47:20 server mysqld[21276]: 
May 16 01:47:20 server mysqld[21276]: See the manual for more instructions.
May 16 01:47:20 server mysqld[21276]: 
May 16 01:47:20 server mysqld[21276]: Please report any problems with the /usr/bin/mysqlbug script!
May 16 01:47:20 server mysqld[21276]: 
May 16 01:47:20 server mysqld[21276]: The latest information about MySQL is available at http://www.mysql.com/
May 16 01:47:20 server mysqld[21276]: Support MySQL by buying support/licenses from http://shop.mysql.com/
May 16 01:47:20 server mysqld[21276]: 
May 16 01:47:20 server mysqld[21309]: 100516  1:47:20 [Note] Plugin 'FEDERATED' is disabled.
May 16 01:47:20 server mysqld[21309]: 100516  1:47:20  InnoDB: Started; log sequence number 0 44233
May 16 01:47:20 server mysqld[21309]: 100516  1:47:20  InnoDB: Starting shutdown...
May 16 01:47:21 server mysqld[21309]: 100516  1:47:21  InnoDB: Shutdown completed; log sequence number 0 44233
May 16 01:47:23 server mysqld[21343]: 100516  1:47:23 [Note] Plugin 'FEDERATED' is disabled.
May 16 01:47:23 server mysqld[21343]: 100516  1:47:23  InnoDB: Started; log sequence number 0 44233
May 16 01:47:23 server mysqld[21343]: ERROR: 1064  You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ALTER TABLE user ADD column Show_view_priv enum('N','Y') CHARACTER SET utf8 NOT ' at line 1
May 16 01:47:23 server mysqld[21343]: 100516  1:47:23 [ERROR] Aborting
May 16 01:47:23 server mysqld[21343]: 
May 16 01:47:23 server mysqld[21343]: 100516  1:47:23  InnoDB: Starting shutdown...
May 16 01:47:24 server mysqld[21343]: 100516  1:47:24  InnoDB: Shutdown completed; log sequence number 0 44233
May 16 01:47:24 server mysqld[21343]: 100516  1:47:24 [Note] /usr/sbin/mysqld: Shutdown complete
May 16 01:47:24 server mysqld[21343]: 
May 16 01:47:24 server mysqld[21361]: 100516  1:47:24 [Note] Plugin 'FEDERATED' is disabled.
May 16 01:47:24 server mysqld[21361]: 100516  1:47:24  InnoDB: Started; log sequence number 0 44233
May 16 01:47:24 server mysqld[21361]: 100516  1:47:24  InnoDB: Starting shutdown...
May 16 01:47:25 server mysqld[21361]: 100516  1:47:25  InnoDB: Shutdown completed; log sequence number 0 44233
May 16 01:47:25 server mysqld[21377]: 100516  1:47:25 [Note] Plugin 'FEDERATED' is disabled.
May 16 01:47:25 server mysqld[21377]: 100516  1:47:25  InnoDB: Started; log sequence number 0 44233
May 16 01:47:25 server mysqld[21377]: ERROR: 1050  Table 'plugin' already exists
May 16 01:47:25 server mysqld[21377]: 100516  1:47:25 [ERROR] Aborting
May 16 01:47:25 server mysqld[21377]: 
May 16 01:47:25 server mysqld[21377]: 100516  1:47:25  InnoDB: Starting shutdown...
May 16 01:47:27 server mysqld[21377]: 100516  1:47:27  InnoDB: Shutdown completed; log sequence number 0 44233
May 16 01:47:27 server mysqld[21377]: 100516  1:47:27 [Note] /usr/sbin/mysqld: Shutdown complete
May 16 01:47:27 server mysqld[21377]: 
May 16 01:47:27 server kernel: [34505.390012] type=1505 audit(1273967247.407:65):  operation="profile_replace" pid=21394 name="/usr/sbin/mysqld"
May 16 01:57:32 server kernel: [  118.067013] type=1505 audit(1273967852.815:14):  operation="profile_load" pid=996 name="/usr/sbin/mysqld"

```

---

### Post by ndstate on 2010-05-18
For the removal of package with errors:

> I dont know if its applicable to your situation or not, but I had similar problems and [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096) fixed it for me.

Good luck

---

### Post by Gehaktbal on 2010-05-20
I gave up. I fixed it by purging mysql-server-5.1 and mysql-common. Afterwards I deleted /var/lib/mysql /etc/mysql and /var/log/mysql

Installing mysql again worked for me. Luckily i had no really really really important data in the databases.

---

### Post by vishnujyothi on 2010-06-05
> **rowinggolfer said:**
> here's what worked for me.

open 2 terminals.
in the first, execute

sudo apt-get remove mysql-server-5.1

when that hangs (because it perpetually loops callng mysqld stop... ) execute this is the 2nd terminal

sudo service mysql start


that seems to free the first terminal process.



Its worked for my friend also, we have been trying to fix this for couple of days,Thanks

---

### Post by jaya28inside on 2010-08-19
> **vishnujyothi said:**
> Its worked for my friend also, we have been trying to fix this for couple of days,Thanks

why I also got 

> 
root@omega:~# sudo service mysql start
start: Job is already running: mysql


but the result was, the 1st terminal 
didn't get end yet.... still stuck on that hang-process

---

### Post by threepwood960 on 2011-02-01
Do you know if there is another way to solve it? I have now the same problem, but I have important data in my databases.

---

