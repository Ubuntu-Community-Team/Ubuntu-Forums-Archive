---
title: "Trying to setup MySQL on Ubuntu 10.04"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by tech_girl on 2010-05-16
I recently downloaded and installed Ubuntu 10.04, and I really like it. 

On my Windows machine, I have a zip version of MySQL. I usually do not use the installer so that I can just delete the folder when it comes to removal of the program.

Im hoping I can do the same for Linux. So I downloaded this particular file "mysql-5.1.46-linux-i686-glibc23.tar.gz" and unzipped the file and followed the instructions. 

I then started mysqld_safe and mysql.server (according to the instruction). It started ok. But when I then tried to login to mysql, it returns a message:

"The program 'mysql' can be found in the following packages:
 * mysql-client-core-5.1
 * mysql-client-5.0
 * mysql-cluster-client-5.1"

What is the issue here? I would have thought "mysql-5.1.46-linux-i686-glibc23.tar.gz" would have contained all the packages. Is there some configuration to be done?

Would appreciate if someone can point me to the right direction? Thanks.

---

### Post by gumrol on 2010-06-14
I had the exact same issue.. I wasn't sure which way to go, install the 5.0 client, or 5.1 - I decided to go 5.1

```
sudo apt-get install mysql-client-5.1
```Now I get this error when trying to connect to mysql:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I think the MySQL upgrade totally broke while upgrading.. trying to sort it out before I can get to work!

Edit: 
I followed a few other threads where people had the same issues.. it seemed from what I gathered, that the mysql server install on my upgrade from Ubuntu 9.10 to 10.04 had failed, and installing sql server again would be necessary & would not delete my current databases. I backed them up just to be sure - backup this folder: /var/lib/mysql.
I then ran:
```
sudo aptitude install mysql-server
```
That installed mysql server (which should have been installed in the upgrade). And I can now connect to my databases again! Really stoked, because I thought I might lose them all. Even though I'd backed them up, its still a mission re-installing all your dev databases.

---

### Post by satish_j on 2010-09-30
am facing the same issue..only diff is iam compiling from source tar file..
Previously,On Hardy heron,it got installed in the first attempt..
Any idea where to post mysql installation issues??i mean any forums on internet where we can get the help on it??

---

