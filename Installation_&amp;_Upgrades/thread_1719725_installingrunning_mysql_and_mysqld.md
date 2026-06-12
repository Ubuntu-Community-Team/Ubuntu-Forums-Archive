---
title: "installing/running mysql and mysqld"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by area5one on 2011-04-02
Hi all,

I'm running Ubuntu 10.10, I just installed mysql like so:

sudo apt-get install mysql

Which installs several packages.. When I try to connect to the database server I write:

> mysql

This returns: ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I think this error means there is no server running. And checking the process list indicates that there is no service called mysqld.

Also, I do:

[~] $sudo start mysql
start: Job is already running: mysql

But this doesn't help anything... any ideas where to start solving this problem?

---

### Post by An Sanct on 2011-04-02
If you are trying to install LAMP (Linux Apache MySQL PHP) then follow [these instructions]("http://www.techtickle.com/install-lamp-ubuntu-maverick-lucid-easy.html") (one command)
```
sudo apt-get install lamp-server^
```

This will also install MySQL and all the needed packages.

To install MySQL only, [follow these instructions]("http://www.zolved.com/synapse/view_content/27986/How_to_install_MySQL_On_Ubuntu").

---

### Post by area5one on 2011-04-02
Thanks for the link... I commented out the bind-address and restarted the server.

I tried:

[~] $sudo service mysql restart
mysql start/running

Starting mysql still gives the same error

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I don't have a mysqld.sock file, can that be part of the problem?

---

### Post by area5one on 2011-04-02
By the way, when I run

ps -ax | grep mysqld

There are no active processes by that name...

---

