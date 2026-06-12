---
title: "Problems with apache localhost/mysql Not Found"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by eAi-T0ky0 on 2008-11-12
Hey all guys :popcorn:

  I was works good with my localhost apache server from my web localhost it open ok!!! I can see the files I put in /var/www ok!! But when I go from the web localhost/mysql or localhost/phpmyadmin to make a new database it  "Not Found" "The requested URL /mysql was not found on this server." :(

I search for phpmyadmin and mysql It was install k and works good see

```
Ezz@ubuntu:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 5.0.51a-3ubuntu5.3 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> 
```

my sql is in >> mysql: /usr/bin/mysql /etc/mysql /usr/share/mysql /usr/share/man/man1/mysql.1.gz

and phpmyadmin >>> phpmyadmin: /etc/phpmyadmin /usr/share/phpmyadmin


I wonder must move this files from /usr/share to /var/www to work or it's wrong?? and what can I do to make it work useful ok!!! It was works good without files in /var/www file ... :(

Thanks

---

