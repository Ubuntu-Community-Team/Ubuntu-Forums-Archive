---
title: "Unable to upgrade MySql on Ubuntu"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by kanav_kapoor on 2014-05-31
I'm following [this]("https://wiki.ampath.or.ke/pages/viewpage.action?pageId=70811889") tutorial to upgrade MySql. But i'm stuck at STEP 4: STARTING THE SERVER AND UPGRADING. Current version of my MySql is 5.1. 


  When i'm trying to write ```
sudo /usr/sbin/mysqld --skip-grant-tables
```, the terminal says ```
sudo: /usr/sbin/mysqld: command not found
```




  Any suggestions?

---

### Post by Ubi_one_2014 on 2014-06-01
you can try to install these packages:
[http://packages.ubuntu.com/trusty/mysql-server-5.6](http://packages.ubuntu.com/trusty/mysql-server-5.6)

not sure what packages you need
probably mysql-server and mysql-common for 5.6

---

