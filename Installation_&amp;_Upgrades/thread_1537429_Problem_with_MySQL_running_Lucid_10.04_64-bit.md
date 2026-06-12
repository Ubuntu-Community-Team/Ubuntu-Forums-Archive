---
title: "Problem with MySQL running Lucid 10.04 64-bit"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2010-07-23
I cannot seem to connect to MySQL since I upgraded from 10.04 32-bit to 10.04 64-bit.  Using MySQL Workbench, I get the message "Cannot Connect to Database Server".  The server is running on 127.0.0.1:3306 (at least Workbench thinks so; I do not show MySQL running under System Monitor, but if I try to start it, I get a message saying it is already running).  I have some Openoffice DB's as well, but when I try to access any of them, I get "the connection could not be established" and a SQL status of 28000 with an error code of 1045.

I have searched the file system for com.mysql.jdbc.Driver, but cannot find it.  I seem to recall when I first set up MySQL under Jaunty I had to configure the driver or connection.  However, I cannot remember what I did.  I only remember something concerning choosing a file that ended in .so.

My searches on Google and Ubuntu forums have proved fruitless.  Help!

---

### Post by cscj01 on 2010-07-23
OK, I figured out the passwords were not the same as I had before.  Now I can connect, but I cannot run any queries.  If I try to run a query, I get a message saying ```
Can't find file: './<database name>/<table name>.frm'
``` where database name and table name are the names of the database I am using and the table name is the first table specified in the query. 

I checked the data directory setting and it is /var/lib/mysql.   The database folder is in /var/lib/mysql and all the tables are in the database folder.

---

### Post by ServerStorm on 2010-07-23
Hi [cscj01]("http://ubuntuforums.org/member.php?u=82488"),

I would recommend that you install webmin ([http://www.webmin.com/](http://www.webmin.com/)) on the computer/server hosting the mysql server.

From there you view and edit most of the mysql configurations. By able to more clearly see the configuration it may give you better insight into resolving your errors.

Regards,
Steve

---

