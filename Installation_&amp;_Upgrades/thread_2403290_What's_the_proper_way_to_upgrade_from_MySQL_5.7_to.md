---
title: "What's the proper way to upgrade from MySQL 5.7 to MariaDB 10.1 on 18.04.1"
date: 2018-10-09
forum: Installation &amp; Upgrades
---

### Post by plazman30 on 2018-10-09
I have a server running in my house and noticed that it still had MySQL 5.7 on it even after I upgraded t0 18.04.  So, I decided to take a crack at upgrading to MariaDB.  Most of the guides I found told to backup my databases, stop mysqld, and then remove mysql-server and mysql-client.  Then install mariadb-server and mariadb-client.

So that's exactly what I did.

And when I tried to start MariaDB, it would would time out and never start.

So, Googling I went.

First recommendation was that apparmor was blocking mariaDB, and to put it in complain mode.  So,  I did that, and mariaDB STILL would not start.

Next suggestion said that putting it in complain mode would not work, and I would need to completely disable apparmor for /usr/sbin/mysqld.  I created the necessary soft link and restarted app armor.  Still would not start, just hung and eventually timed out.

Next I just stopped apparmor and tried to start mariaDB, and again it eventually times out and does not start.

Next Google suggestion was to set a timeout value for it's systemd config file and let it finish starting up.  I did that, started up mariaDB, and walked out the door to pick up my kids from school.  45 minutes later, i am staring at a cursor because the command 'sudo systemctl mysqld start' is still hung.

I then decide to uninstall mariadb and reinstall it.  That had zero effect on the problem.  Still hanging.

Did a mysql_upgrade and it completed without issue, but MariaDB again failed to start.

At this point, I had invested well over 2 hours trying to get this to work.  So, I remove MariaDB, reinstalled MySQL, and restored my database files from their backup directory and mysqld fire right up.

What exactly was i doing wrong?

---

### Post by snowy16 on 2019-01-13
18.04.1 uses MariaDB 10.1 as its latest build.  This is incompatible with MySQL 5.7.  You'll need to go up to at least MariaDB 10.2 for the upgrade to work successfully.  You can do that by adding MariaDB's external ubuntu repository which will then install version 10.2 for you.

You can visit this site to view a compatibility chart between MySQL and MariaDB versions -> [https://mariadb.com/kb/en/library/mariadb-vs-mysql-compatibility/#replication-compatibility]("https://mariadb.com/kb/en/library/mariadb-vs-mysql-compatibility/#replication-compatibility")

---

