---
title: "TokuDB fails to load in MariaDB after upgrade from 13.10 to 14.04 server"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by ascom on 2014-04-24
Earlier, I upgraded my website server to Ubuntu 14.04 LTS. I had a very nice setup with MariaDB and the TokuDB engine. However, the setup was kind of messed up when TokuDB refused to load properly, causing WordPress to display the install page because it could not read the database tables! Agh! (Hopefully they are still there...)

I [disabled transparent hugepages]("http://unix.stackexchange.com/questions/99154/disable-transparent-hugepages") (because they were enabled after the upgrade), but TokuDB still refuses to load, even when I followed the [directions on the MariaDB website]("https://mariadb.com/kb/en/how-to-enable-tokudb-in-mariadb/"):

```

MariaDB [(none)]> install soname 'ha_tokudb';
ERROR 1123 (HY000): Can't initialize function 'TokuDB'; Plugin initialization function failed.
```

What else could be causing TokuDB to not load?
[SIZE=1]
(copied from the unix stack exchange for a faster answer...)

[/SIZE][SIZE=1][/SIZE]**UPDATE:** I have fixed the issue. See here for more information: [https://mariadb.atlassian.net/browse/MDEV-6165](https://mariadb.atlassian.net/browse/MDEV-6165)

---

### Post by sbrown-o on 2014-04-26
I had the same issue while upgrading to 14.04. However, I was using MariaDB 10.0.8 with TokuDB. When I upgraded, the TokuDB Enging starting having the same problems as described above. After trying the fix mentioned in UPDATE above and 5 hours of other attempts to get this fixed, I finally got it working (as well as upgrading mariadb to 10.0.10) by purging (not just removing) mariadb.


These are the steps I took that FINALLY got it working. Not all commands may be necessary, but this is what, in the end, worked for me.


Purge MariaDB ***Make sure to backup any config changes you may have made as the config files will be removed***
```
sudo apt-get update
sudo apt-get -y purge mariadb* 
sudo apt-get -y autoremove
sudo apt-get clean
```
Then I removed the mariadb repo entries in sources.list (**/etc/apt/sources.list**) and started over following the docs: [https://downloads.mariadb.org/mariadb/repositories/](https://downloads.mariadb.org/mariadb/repositories/)
```
sudo apt-get install software-properties-common
sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db
sudo add-apt-repository 'deb http://mirror.jmu.edu/pub/mariadb/repo/10.0/ubuntu trusty main'
sudo apt-get update
sudo apt-get install mariadb-server
```
Next, edit **/etc/mysql/conf.d/tokudb.cnf** and uncomment the following > plugin-load-add=ha_tokudb.so
Restart the server and hope it works!
```
sudo service mysql restart
```


Hopefully this will work for you as well.

---

### Post by ascom on 2014-04-26
Actually, it was caused by the previous version not shutting down gracefully (the init script failed?), combined with the new version of TokuDB refusing to upgrade the databases when it didn't see a clean shutdown.

---

### Post by sbrown-o on 2014-04-26
Weird. 
I tried following the fix on the page you liked to ([https://mariadb.atlassian.net/browse/MDEV-6165](https://mariadb.atlassian.net/browse/MDEV-6165)). It didn't work with any version. I originally had MariaDB 10.0.8 before upgrading to Ubuntu 14.0.4.
I tried it with MariaDB 10.0.8, 10.0.9, and 10.0.10. None of it wanted to work, even after attempting the fix from the link above. Just needed a complete purge and reinstall. But on the reinstall, the new version of MaraiDB (from 10.0.8 to 10.0.10) everything seems to work great now.

Oh and I should mention that ALL of my error logs were empty. There was not a single error output to any of the mysql log files, which I thought was very add as well.

---

### Post by ascom on 2014-04-26
I guess our cases are different...at least my MariaDB is working now.

---

