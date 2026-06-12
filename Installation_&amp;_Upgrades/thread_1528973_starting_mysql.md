---
title: "starting mysql"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by acognard on 2010-07-11
Hi all, i am trying to instal mysql but unsuccessfully.
 
plse, find below my try :
pceib:/etc# apt-get install mysql-server
Lecture des listes de paquets... Fait
Construction de l'arbre des dÃ©pendances
Lecture des informations d'Ã©tat... Fait
mysql-server est dÃ©jÃ la plus rÃ©cente version disponible.
0 mis Ã jour, 0 nouvellement installÃ©s, 0 Ã enlever et 86 non mis Ã jour.
pceib:/etc# /etc/init.d/mysql status
MySQL is stopped..
pceib:/etc# /etc/init.d/mysql start
Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!
 
debian-start, my.cnf are empty
& /var/run/mysqld does not exists. 
I 've added manualy an empty mysqld.sock file , but same result.
 
some tryies : 
pceib:/etc# ps auxww |grep mysqld
root 4470 0.0 0.8 3144 784 pts/2 S+ 20:38 0:00 grep mysqld
 
pceib:/etc# mysql_install_db
 
and the result is 
pceib:/etc# /etc/init.d/mysql start
Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!
 
using root, 'vi /etc/my.cnf' says it is empty
pceib:/etc# ls -l my*
total 16
drwxr-xr-x 2 root root 4096 jun 1 22:28 conf.d
-rw------- 1 root root 312 jun 1 22:28 debian.cnf
-rwxr-xr-x 1 root root 1198 fÃ©v 13 11:56 debian-start
-rw-r--r-- 1 root root 3868 jun 1 23:42 my.cnf
 
 
any help ?
Tks in advance.

---

### Post by alexshr on 2010-07-11
first try "sudo apt-get update"

then try with "sudo apt-get install mysql-client-core-5.1"

I suggest you try to install the mysql from the synaptic packet manager.

---

### Post by acognard on 2010-07-11
tks for your reply , finaly i uninstalled et installed it again.
sincerly.
Arnaud

---

