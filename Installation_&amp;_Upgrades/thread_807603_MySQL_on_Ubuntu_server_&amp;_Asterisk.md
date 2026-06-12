---
title: "MySQL on Ubuntu server &amp; Asterisk"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-05-25
I have replaced a SuSE server with an Ubuntu 8.04 server.

The server runs MySQL, which is working locally. My Asterisk server (192.168.1.20) should access this MySQL server (192.168.1.254). I have left on the Asterisk server my old settings:
[general]
dbhost = 192.168.1.254
dbname = myasterisk
dbuser = myastuser
dbpass = myastpass
dbport = 3306
dbsock = /var/lib/mysql/mysql.sock

In MySQL I have setup a record with

INSERT INTO `user` (`Host`, `User`, `Password`, `Select_priv`, `Insert_priv`, `Update_priv`, `Delete_priv`, `Create_priv`, `Drop_priv`, `Reload_priv`, `Shutdown_priv`, `Process_priv`, `File_priv`, `Grant_priv`, `References_priv`, `Index_priv`, `Alter_priv`, `Show_db_priv`, `Super_priv`, `Create_tmp_table_priv`, `Lock_tables_priv`, `Execute_priv`, `Repl_slave_priv`, `Repl_client_priv`, `Create_view_priv`, `Show_view_priv`, `Create_routine_priv`, `Alter_routine_priv`, `Create_user_priv`, `ssl_type`, `ssl_cipher`, `x509_issuer`, `x509_subject`, `max_questions`, `max_updates`, `max_connections`, `max_user_connections`) VALUES
('192.168.1.20', 'root', '**********************', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', '', '', '', '', 0, 0, 0, 0);


However, the remote client (*.20) cannot connect to the server (*.254):

[May 26 11:50:21] ERROR[3096]: res_config_mysql.c:651 mysql_reconnect: MySQL RealTime: Failed to connect database server myasterisk on 192.168.1.254 (err 2003). Check debug for more info.

What do I miss?

bye

Ronald

---

### Post by ELMIT on 2008-05-26
I came a big step ahead, but still not all working.

With /etc/mysql/my.cnf
bind-address = 192.168.1.254

and 

/etc/hosts.allow
mysqld: 192.168.1.0/255.255.255.0
mysql: 192.168.1.0/255.255.255.0

and 

in mysql's database mysql.user   change the field password to OLD_PASSWORD

my Asterisk server can connect to the database server.


HOWEVER. the database server includes also a web server, which database WAS reachable at 127.0.0.1. Since I changed my.cnf to bind-address=192.168.1.254  it cannot connect to the database anymore.


I tried to use bind-address=0.0.0.0 with no success for localhost, but Asterisk still can connect.
telnet localhost 3306 allows me also to connect, just not apache2.

What is the last missing piece to get that to work, so that the database can be accessed local and remote?

---

