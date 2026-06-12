---
title: "Uninstall of packages causes my mysql connections to break"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by espressobeanie on 2011-04-22
I just 'auto-removed' a lot of packages after uninstalling 'x-server-org-core', 'gdm3', and 'gnome-core' and somehow I bricked my web forum setup that relies on mysql. I'm not sure what to do, or how to begin troubleshooting what the problem is. I keep getting the following error when I try to login into it:

> General Error

            SQL ERROR [ mysqli ]

Lost connection to MySQL server at 'reading initial communication packet', system error: 0 [2013]

An sql error occurred while fetching this page. Please contact an administrator if this problem persists.
        
    
    
I checked to make sure that I had php5-mysql, php5, mysql-client, and mysql-server still installed, and I did. However, I'm not sure what I did, but an 'auto-remove' some random package completely messed up my forum. Does anyone know how I can go about troubleshooting what the real problem is?

---

### Post by sanguinoso on 2011-04-22
post the results of this command here:

```
ps aux | grep mysqld
```

All it does is check to see if mysqld is running.

---

### Post by espressobeanie on 2011-04-22
I can't copy and paste from screen, but here goes:

```
root    2108    0.0   0.0  3952       612 ?     S   15:39   0:00   /bin/sh /usr/bin/mysqld_safe

mysql 2228   0.4   2.8   171116  29488 ?  S1 15:39   0:00   /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket-/var/run/mysqld/mysqld.sock 
--port=3306

root    2229   0.0    0.0  3852      624 ?     S    15:39   0:00  logger -t mysqld -p daemon.error

root   2869    0.0    0.0   7548      828 tty1 S+ 15:40   0:00  grep mysqld
```I can rule out the last one as the command I just entered. I also get stuff popping up saying that warning: mysql.sh' missing LSB tags and overrides. I can still access mysql, but I'm wondering if there's a way to somehow backup the mysql databases and reinstall everything.

---

### Post by sanguinoso on 2011-04-22
Try typing ```
sudo killall mysqld
``` This will force the mysql daemon to restart. To reinstall you cant type ```
sudo apt-get --reinstall install mysql-server
``` This will not destroy any databases you have but its a good idea to keep database backups anyways!

---

