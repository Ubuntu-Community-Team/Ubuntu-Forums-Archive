---
title: "mysql-server problems!! Please help!!!"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by kernel1 on 2007-11-29
Hi i am confused ;(

When I type: mysql i got this: ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

So i want to uninstall it to install it again and to set new root password and after to install phpmyadmin.

When I try to remove mysql server I get this error:

apt-get remove mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libdbi-perl libdbd-mysql-perl mysql-server-5.0
  mysql-client-5.0 libplrpc-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mysql-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 86.0kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 159787 files and directories currently installed.)
Removing mysql-server ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help me!!!

Thanks

---

### Post by Diabolis on 2008-04-15
at terminal:
```

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
```

then go here:
system / preferences / synaptic package manager / edit / fix broken packages

After that try to install again mysql.

---

