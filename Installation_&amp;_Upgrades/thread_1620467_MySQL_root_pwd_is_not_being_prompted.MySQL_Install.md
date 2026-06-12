---
title: "MySQL root pwd is not being prompted.MySQL Installation terminates abruptly"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by nikhilsista on 2010-11-13
Hello All,

I've encountered the following exception while installing mySql database as part of the LAMP installation.

The mySql database installation is getting abruptly terminated !!!!!!! Here is the trace !

**nikhil@nikhil-laptop:~$ sudo apt-get install mysql-server**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 69 not upgraded.
Need to get 0B/94.6kB of archives.
After this operation, 131kB of additional disk space will be used.
Selecting previously deselected package mysql-server.
(Reading database ... 191949 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.1.41-3ubuntu12.7_all.deb) ...
Setting up mysql-server (5.1.41-3ubuntu12.7) ...[COLOR=Red]          [From here on it's not proceeding further)[/COLOR]
**nikhil@nikhil-laptop:~$ cd /var/lib**

It hasn't prompted me for the root password. During the installation of phpmyAdmin as part of the LAMP installation, it prompts for mySQL database root password, but since the installation is getting terminated abruptly, I'm not able to set root password because of which I'm not able to install & setup the MYSQL database.

Following is the exception I'm encountering when I'm trying to set a root password or hit "ENTER" when the password is being prompted !

**nikhil@nikhil-laptop:/var/lib$ mysqladmin -u root password 'mynewpassword'**
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


Appreciate your help !

Cheers
Nikhil

---

