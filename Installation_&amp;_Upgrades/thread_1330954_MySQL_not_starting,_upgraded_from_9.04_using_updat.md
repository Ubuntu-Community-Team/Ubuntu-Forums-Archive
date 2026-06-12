---
title: "MySQL not starting, upgraded from 9.04 using update-manager"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by WesleyWex on 2009-11-18
I just upgraded from Ubuntu 9.04 to 9.10. My last installation was already updated before the upgrade and I didn't use apt-get, performed the upgrade trough the GUI update-manager.

Now after the reboot I noticed two things: MySQL is not starting ([fail] and no log on /var/log/mysql.err or /var/log/mysql.log), and a conflict on apt:

mysql-server-5.0 depends upon mysql-server-core-5.0
mysql-server-core-5.1 conflicts with mysql-server-core-5.0

What the hell happened? The [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/910") clearly say:
> Performing an upgrade via update-manager will correctly handle the transition from MySQL 5.0 to MySQL 5.1.

---

### Post by wojox on 2009-11-18
Try the Check Tables Function:

```
sudo mysql_upgrade --force -uroot -p
```

And then:

```
sudo service mysql restart
```

---

### Post by WesleyWex on 2009-11-18
MySQL fails to load:
```
wesley@Jupiter:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                                               [fail]
```

So this command fails too:
```
wesley@Jupiter:~$ sudo mysql_upgrade --force -uroot -p
Enter password:
Looking for 'mysql' as: mysql
Looking for 'mysqlcheck' as: mysqlcheck
Running 'mysqlcheck' with connection arguments: '--port=3306' '--socket=/var/run/mysqld/mysqld.sock'
mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect
FATAL ERROR: Upgrade failed
```

---

### Post by WesleyWex on 2009-11-18
Ok, since I can't wait that long for the POSSIBILITY of someone helping me, I did the following:

[LIST=1]
[*]Purged MySQL trough apt-get purge mysql-server-5.1 mysql-server-core-5.1
[*]Installed MySQL 5.0 trough apt-get install mysql-server-5.0
[*]Stopped MySQL
[*]Moved /var/lib/mysql to /var/lib/mysql.old
[*]Copied the backup with -a of /var/lib/mysql
[*]Copied the backup with -a of /etc/mysql/debian.cnf
[*]Copied the backup with -a of /etc/mysql/my.cnf
[*]Started MySQL
[/LIST]

Have in mind this was only possible because I had a backup for /var/lib/mysql and /etc/mysql from before the upgrade.

This is only one of my problems, rtorrent doesn't watch folders anymore and shorewall was removed and I was left without a replacement, had to manually figure out that shorewall6 works for me.

That was the most disappointing upgrade I have ever made on Ubuntu. :mad:

---

### Post by gfroese on 2010-01-22
I ran 'do-release-upgrade' and the same thing happened to me and I believe it was because I chose not to upgrade the mysql config files during the upgrade.

After getting some great help from the people in #mysql on freenode IRC, I was able to get up and running again.

All I had to do was comment out the following line in /etc/mysql/my.cnf:

skip-bdb
   changed to
#skip-bdb

After that I was able to start mysql again and continue where I left off.

---

### Post by agampher on 2010-02-27
> **gfroese said:**
> I ran 'do-release-upgrade' and the same thing happened to me and I believe it was because I chose not to upgrade the mysql config files during the upgrade.

After getting some great help from the people in #mysql on freenode IRC, I was able to get up and running again.

All I had to do was comment out the following line in /etc/mysql/my.cnf:

skip-bdb
   changed to
#skip-bdb

After that I was able to start mysql again and continue where I left off.

Awesome.  Thanks for this, gfroese.  Worked like a champ.

---

