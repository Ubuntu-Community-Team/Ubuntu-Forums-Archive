---
title: "mysql"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by Rakeshvijayan on 2010-12-02
Hi friends

I tried to install koha library management  I installed lamp-server and needed services but when i try to connect 
mysql following messages appear 

 ```
 rakesh@ubuntu:~$ mysql -uroot -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
rakesh@ubuntu:~$ mysql -uroot -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
rakesh@ubuntu:~$ mysql
ERROR 1045 (28000): Access denied for user 'rakesh'@'localhost' (using password: NO)
rakesh@ubuntu:~$ nets
netscsid  netstat   
rakesh@ubuntu:~$ netstat -ln | grep mysql
unix  2      [ ACC ]     STREAM     LISTENING     5206     /var/run/mysqld/mysqld.sock
rakesh@ubuntu:~$ iptables
iptables v1.4.4: no command specified
Try `iptables -h' or 'iptables --help' for more information.

```

---

