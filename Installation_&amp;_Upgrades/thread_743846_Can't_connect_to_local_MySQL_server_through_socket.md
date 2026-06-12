---
title: "Can't connect to local MySQL server through socket '/var/run/mysq"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by darkoysm on 2008-04-03
I'm trying to to install Apache, PHP, and mysql. I installed everything but i ran into trouble with mysql, cause i havent been able to connect to the server at all, everytime i try to connect i get the message:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

there doesnt seem to be a mysqld directory in /var/run and i tried whereis mysqld.sock, i got nothing in return. I should mention that i installed all the packages from synaptic manager. i'm running ubuntu 7.10

---

### Post by windsofhell on 2008-04-03
Have you tried to find the mysql.sock somewhere? It could be in placed in a different location.
Are you sure the mysql is running ?

What you can do is:

start up your mysql and see where it is creating the mysql.sock

and then create a configuration file in our home with this name .my.cnf

which contains: 

[client]
socket        <location of mysql.sock>

//Daniel

---

### Post by darkoysm on 2008-04-03
mysql is not starting, the only mysql folder i can find is in /etc/ and it my.cnf is there, i'm getting that message every time i try to run mysql in command prompt. How can i locate mysqld.sock????? where???

---

### Post by windsofhell on 2008-04-03
The mysqld.sock is created when you start the mysql daemon.
Try starting the mysql daemon by hand, you can find the "mysqld"  at <your mysql installation dir>/bin

---

