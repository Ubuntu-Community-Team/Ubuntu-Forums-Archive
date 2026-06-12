---
title: "Mysql 5.1.44 installation"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by mosty friedman on 2010-03-15
hey everyone, 

I am trying to install mysql 5.1.44..so i downloaded the binary package, i extracted it and then followed the instructions that were in the manual but i keep getting this error when running this command

```

scripts/mysql_install_db --basedir=/home/mosty/mysql

```

the error is 

```

Installing MySQL system tables...
100315 20:07:27 [Warning] Can't create test file /var/lib/mysql/mosty.lower-test
100315 20:07:27 [Warning] Can't create test file /var/lib/mysql/mosty.lower-test
100315 20:07:27 [ERROR] /home/mosty/mysql/bin/mysqld: Can't find file: './mysql/db.frm' (errno: 13)
ERROR: 1017  Can't find file: './mysql/db.frm' (errno: 13)
100315 20:07:27 [ERROR] Aborting

100315 20:07:27 [Note] /home/mosty/mysql/bin/mysqld: Shutdown complete


Installation of system tables failed!  Examine the logs in
/var/lib/mysql for more information.

You can try to start the mysqld daemon with:

    shell> /home/mosty/mysql/bin/mysqld --skip-grant &

and use the command line tool /home/mosty/mysql/bin/mysql
to connect to the mysql database and look at the grant tables:

    shell> /home/mosty/mysql/bin/mysql -u root mysql
    mysql> show tables

Try 'mysqld --help' if you have problems with paths.  Using --log
gives you a log in /var/lib/mysql that may be helpful.

The latest information about MySQL is available on the web at
http://www.mysql.com/.  Please consult the MySQL manual section
'Problems running mysql_install_db', and the manual section that
describes problems on your OS.  Another information source are the
MySQL email archives available at http://lists.mysql.com/.

Please check all of the above before mailing us!  And remember, if
you do mail us, you MUST use the /home/mosty/mysql/scripts/mysqlbug sc

```

any ideas???

---

### Post by phillw on 2010-03-15
If you're installing LAMP, there is no need to go get the packages one by one.

From Ubuntu 9.10 onwards, simply use ```
sudo tasksel
``` and select the LAMP installation option. After that, use synaptics to put on PhpMyAdmin.

It's covered a bit more in a posting I wrote over here -->[http://forum.phillw.net/viewtopic.php?f=4&t=4](http://forum.phillw.net/viewtopic.php?f=4&t=4)

Regards,

Phill.

---

