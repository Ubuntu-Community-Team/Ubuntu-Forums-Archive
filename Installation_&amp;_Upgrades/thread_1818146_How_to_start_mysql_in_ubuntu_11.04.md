---
title: "How to start mysql in ubuntu 11.04?????"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by Drazer on 2011-08-04
Hello frends i am new to ubuntu.
I wana start mysql but its not working! error occurs!
"[COLOR=Red]
root@drazer-GA-MA785GM-US2H:/etc/init.d# mysql.server start
mysql.server: command not found
root@drazer-GA-MA785GM-US2H:/etc/init.d# mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
root@drazer-GA-MA785GM-US2H:/etc/init.d# mysql start
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
root@drazer-GA-MA785GM-US2H:/etc/init.d# 

[/COLOR]"
I have installed mysql client and server packages.
pls help.:(

---

### Post by 1 clue is enough on 2011-08-04
If you installed via apt-get or Synaptic you should be able to:
$ mysql -u root -p
it asks for your password and enter it...now you're in.
mysql>

---

### Post by fdrake on 2011-08-04
> root@drazer-GA-MA785GM-US2H:/etc/init.d# mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: 

1. try not to be always logged as root user in linux(root@). you don't need to be root user in linux to run mysql
2.see link on how to connect to mysql
[http://dev.mysql.com/doc/refman/5.0/en/connecting-disconnecting.html](http://dev.mysql.com/doc/refman/5.0/en/connecting-disconnecting.html)

---

### Post by Blasphemist on 2011-08-04
You should also be able to get access using phpmyadmin.

---

### Post by Drazer on 2011-08-04
Thanks Guys...

---

