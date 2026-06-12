---
title: "ApacheMySQLPHP guide : out of date or not fully tested ?"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2006-08-05
I am trying to setup Apache2, PHP5 and Mysql. I did a bit of search in these forums but there are so many posts with different approaches and solutions that it is starting to get very confusing.  I tried one thread and something from the Ubuntu community docs. But it doesn't seam to work. I think its because the doc is either not updated, not tested or simply wrong. My knowledges on Ubuntu are limited as I started using it this year. 


**From a post I found, I did this :**

sudo aptitude -y purge apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql apache2-common

sudo aptitude -y install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql apache2-common



**And then following this other link I found :**

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
(is this guide updated and verified ?)

**A few errors I encountered following that guide :**

1) at "**After installing PHP**", it says to increase memory by editing a file /etc/php5/apache2/php2.ini but that file doesn't exist !  I am assuming it is php.ini instead that I have to edit. Right ?
 
[INDENT]$ ls -al /etc/php5/apache2
total 88
drwxr-xr-x 2 root root  4096 2006-08-03 22:45 .
drwxr-xr-x 3 root root  4096 2006-07-30 10:09 ..
-rw-r--r-- 1 root root 40543 2006-08-03 22:51 php.ini
-rw-r--r-- 1 root root 40541 2006-08-03 22:25 php.ini~[/INDENT]

so I updated to => memory_limit = 256M


2) At the chapter "**After installing MySQL**", I do :
[INDENT]cd /usr
sudo ./bin/mysql_install_db --user=mysql[/INDENT]

There is a note on the guide right after that, not sure if I should have done this or not  ?

**[INDENT]that command is not needed for Ubuntu 6.06 (Dapper Drake). Is it needed for Breezy?[/INDENT]**


Anyway, doing it shows a bunch of output text including :

[INDENT]PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:
/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h browserice-desktop password 'new-password'
See the manual for more instructions.

NOTE:  If you are upgrading from a MySQL <= 3.22.10 you should run
the /usr/bin/mysql_fix_privilege_tables. Otherwise you will not be
able to use the new GRANT command!

You can start the MySQL daemon with:
cd /usr ; /usr/bin/mysqld_safe &[/INDENT]



Then it says I have to do **mysql -u root** but I get :
[INDENT]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/INDENT]

Why does the guide says to do it this way when in the output text shown above, it says otherwise ? The text says to start Mysql and then changing the password. But if I do start it like it says, I get :

[INDENT]browserice@browserice-desktop:/usr$ cd /usr ; /usr/bin/mysqld_safe &
[1] 9547
browserice@browserice-desktop:/usr$ Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[9605]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[9614]: ended
[it waits for a command to be entered]
[/INDENT]

I checked and there is no such file. Anyway, since the guide expects the next step to be at the mysql command line and that seams to be where I am now, I do :
[INDENT]SET PASSWORD FOR 'root'@'localhost' = PASSWORD('xxxxxxx');[/INDENT]

But I get :
[INDENT]bash: syntax error near unexpected token `('
[1]+  Done                    /usr/bin/mysqld_safe[/INDENT]


At this point, I prety much quit.

I am finding that instead of having multiple posts from just about anyone about how to do it and indicating different ways to do it, why not update THIS guide once and for all so we would stop searching for answers on how to do it and how to fix problems ????

It doesn't make sense to have an outdated or untested guide and 100 different posts on how to do it. This information should be centralized in this document or the WIKI so people wouldn't have to go through several posts.

So bottom line, I still want this thing to work but don't want to waste my time reading 100 posts and a guide that just doesn't work. After all, I have seen so many people stating that they are having problems installing this thing up. All I am asking, is one single place for everyone that would finaly show it the right way for everyone to stop wasting time.

---

### Post by Browser_ice on 2006-08-05
I also tried the WIKI but had [problems]("http://www.ubuntuforums.org/showthread.php?t=225931") there too.

---

### Post by az on 2006-08-05
> **Browser_ice said:**
> I am trying to setup Apache2, PHP5 and Mysql. I did a bit of search in these forums but there are so many posts with different approaches and solutions that it is starting to get very confusing.  I tried one thread and something from the Ubuntu community docs. But it doesn't seam to work. I think its because the doc is either not updated, not tested or simply wrong. My knowledges on Ubuntu are limited as I started using it this year. 

A few weeks ago, there was no up-to-date documentation for Dapper anywhere.


> **Browser_ice said:**
> 

**And then following this other link I found :**

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
(is this guide updated and verified ?)

Yes, it is up-to-date and verified by a lot of people.  I made a lot of changes to the page and mentioned what I had doe to the docteam.  I got may suggestions.


> **Browser_ice said:**
> 


**A few errors I encountered following that guide :**

1) at "**After installing PHP**", it says to increase memory by editing a file /etc/php5/apache2/php2.ini but that file doesn't exist !  I am assuming it is php.ini instead that I have to edit. Right ?
 
[INDENT]$ ls -al /etc/php5/apache2
total 88
drwxr-xr-x 2 root root  4096 2006-08-03 22:45 .
drwxr-xr-x 3 root root  4096 2006-07-30 10:09 ..
-rw-r--r-- 1 root root 40543 2006-08-03 22:51 php.ini
-rw-r--r-- 1 root root 40541 2006-08-03 22:25 php.ini~[/INDENT]

so I updated to => memory_limit = 256M


That was a typo.  I fixed it.  Anybody can edit the wiki - I am surprised no one else found it.

> **Browser_ice said:**
> 
2) At the chapter "**After installing MySQL**", I do :
[INDENT]cd /usr
sudo ./bin/mysql_install_db --user=mysql[/INDENT]

There is a note on the guide right after that, not sure if I should have done this or not  ?

**[INDENT]that command is not needed for Ubuntu 6.06 (Dapper Drake). Is it needed for Breezy?[/INDENT]**


Anyway, doing it shows a bunch of output text including :

[INDENT]PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:
/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h browserice-desktop password 'new-password'
See the manual for more instructions.

NOTE:  If you are upgrading from a MySQL <= 3.22.10 you should run
the /usr/bin/mysql_fix_privilege_tables. Otherwise you will not be
able to use the new GRANT command!

You can start the MySQL daemon with:
cd /usr ; /usr/bin/mysqld_safe &[/INDENT]

I am not sure why someone put that there.  As stated, you do not need to do that for Dapper.  You should therefore ignore the messages you get after you run that command.  

I think that script gets run by the package installation scripts, so running it again is not neccessary.

I do not have a breezy system handy, so I can't tell if it is needed for breezy.  If someone knows, they should edit that page.  Since I didn't know, I left it there.


> **Browser_ice said:**
> 

Then it says I have to do **mysql -u root** but I get :
[INDENT]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/INDENT]

Why does the guide says to do it this way when in the output text shown above, it says otherwise ? The text says to start Mysql and then changing the password. But if I do start it like it says, I get :

[INDENT]browserice@browserice-desktop:/usr$ cd /usr ; /usr/bin/mysqld_safe &
[1] 9547
browserice@browserice-desktop:/usr$ Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[9605]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[9614]: ended
[it waits for a command to be entered]
[/INDENT]


Mysqld should already be running.  You do not have to start it.

> **Browser_ice said:**
> 
I checked and there is no such file. Anyway, since the guide expects the next step to be at the mysql command line and that seams to be where I am now, I do :
[INDENT]SET PASSWORD FOR 'root'@'localhost' = PASSWORD('xxxxxxx');[/INDENT]

But I get :
[INDENT]bash: syntax error near unexpected token `('
[1]+  Done                    /usr/bin/mysqld_safe[/INDENT]


At this point, I prety much quit.

Did you make a typo?  It works for me if I cut and paste it.

> **Browser_ice said:**
> 

I am finding that instead of having multiple posts from just about anyone about how to do it and indicating different ways to do it, why not update THIS guide once and for all so we would stop searching for answers on how to do it and how to fix problems ????

It doesn't make sense to have an outdated or untested guide and 100 different posts on how to do it. This information should be centralized in this document or the WIKI so people wouldn't have to go through several posts.

So bottom line, I still want this thing to work but don't want to waste my time reading 100 posts and a guide that just doesn't work. After all, I have seen so many people stating that they are having problems installing this thing up. All I am asking, is one single place for everyone that would finaly show it the right way for everyone to stop wasting time.

I agree.  A few weeks ago, there were dozens of new questions about this.  That's why I gave that page some love.  If anyone has anything to add to it (and there are people who do add to it), please do.

However, I don't know what you did other that those instructions, but they do work for me and many other people.

---

