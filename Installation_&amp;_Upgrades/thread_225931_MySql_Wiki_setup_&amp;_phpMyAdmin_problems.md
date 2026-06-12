---
title: "MySql Wiki setup &amp; phpMyAdmin problems"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2006-07-30
I have two problems :

1) seting up MySqlServer via the 6.06 Wiki
I have a problem at one of its step and don't know what to do 

>mysqladmin -u root password XXXXXXXXX
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'



2) connecting to phpMyAdmin (PHP5) the first time

After installing it, it says to connect to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) but when I do, it asks for a user and password. I haven't seen any notes indicating what I should use there or how I should have set these things up before heading there.

---

### Post by Browser_ice on 2006-07-31
Anyone ?

---

### Post by Browser_ice on 2006-08-03
no answers after 2 days ?

---

### Post by Browser_ice on 2006-08-03
z

---

### Post by az on 2006-08-05
> **Browser_ice said:**
> I have two problems :

1) seting up MySqlServer via the 6.06 Wiki
I have a problem at one of its step and don't know what to do 

>mysqladmin -u root password XXXXXXXXX
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'



2) connecting to phpMyAdmin (PHP5) the first time

After installing it, it says to connect to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) but when I do, it asks for a user and password. I haven't seen any notes indicating what I should use there or how I should have set these things up before heading there.

1-  You alreasy set a root password.  You need to run mysqladmin with a -p switch to enter the password.

2-  Use the mysql root user or create another user.
[https://help.ubuntu.com/community/ApacheMySQLPHP#](https://help.ubuntu.com/community/ApacheMySQLPHP#)

---

