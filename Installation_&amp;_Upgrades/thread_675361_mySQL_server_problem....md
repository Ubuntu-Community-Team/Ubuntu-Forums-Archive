---
title: "mySQL server problem..."
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by Saponsky09 on 2008-01-22
I installed mySQL server 5.0 using synaptic and the installation process went pretty well.  I installed also the mysql GUI client, during installation it asked for a root password (the GUI client) and I set the password.  Now I try to connect to the server or try to set the root account password but I keep getting this error...
```

stockboy@kurosaki-desktop:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

Also if I try to connect as another user...
```

ERROR 1045 (28000): Access denied for user 'stockboy'@'localhost' (using password: NO)
```

I keep getting the same error if I try to set the root account and password, it just won't let me do it.

Please I need help about this, I've got a homework to do!  ;-(

---

### Post by eggdeng on 2008-01-22
Try (exactly)
```
mysql -uroot -p
```
and you should be prompted for your password.

If this fails, try
```
mysql -uroot mysql
```
Then
```
mysql.user set password = password("your_password") where user = "root"
```
then
```
flush privileges
```
then
```
quit
```
and try the original command again.

---

### Post by Saponsky09 on 2008-01-22
THANKS A LOT! It worked, Apparently I was making a syntax error with the commands.  I guess the guide I was following is either erroneous or outdated, i think it's the latter, the guide assumed the server installed with no password by default.   Thank you very much.

---

