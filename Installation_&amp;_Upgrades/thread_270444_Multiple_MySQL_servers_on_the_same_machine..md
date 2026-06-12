---
title: "Multiple MySQL servers on the same machine."
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by Parama on 2006-10-03
***Don't bother answering this - I found a solution and will soon post a guide on how to setup multiple mysql services (from standard aptitude install)*** 

Hi All,

We are running multiple software solutions that uses MySQL and I'm trying to setup a server dedicated for MySQL with multiple database instances (in order to be able to change database instance variables on one instance without touching the other). 

I read another post ([http://ubuntuforums.org/showthread.php?t=250513](http://ubuntuforums.org/showthread.php?t=250513)) but that really doesn't help.

On our current Trustix Linux servers I have set it up via mysql_multi directly in the /etc/my.cnf. However, it's kinda annoying that you cannot stop and start the services independently from each other.

I have:
[LIST][*]Copied /etc/mysql/* to /mysql/mysql3301/*[*]Chown -R mysql.mysql /mysql[*]Changed /mysql/mysql3301/my.cnf (datadir=/mysql/mysql3301/data)[*]Copied /etc/init.d/mysql to /etc/init.d/mysql3301 
[/LIST]
But then it comes to changing the /etc/init.d/mysql3301 startup script: 
I have changed all /etc/mysql to /mysql/mysql3301 but it seems like it doesn't read the /mysql/mysql3301/my.cnf file.
I have also changed the /usr/bin/mysqld_safe to /usr/bin/mysqld, with no result.

When I run ```
sudo /etc/init.d/mysql3301 start
``` it prints som dots vertically and says ```
...failed or took more than 6s
         Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld3301.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld3301.sock' exists!


``` 

Any help is appreciated.

//parama

---

### Post by rdenatale on 2007-03-17
> **Parama said:**
> ***Don't bother answering this - I found a solution and will soon post a guide on how to setup multiple mysql services (from standard aptitude install)*** 
//parama

Did you ever post this???

---

