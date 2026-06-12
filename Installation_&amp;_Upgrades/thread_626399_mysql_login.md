---
title: "mysql login"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by june_c21 on 2007-11-29
when i type mysql -u root mysql , it prompt this error " ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"  

what this mean?

2nd question - how to make sure mysql is install in my pc?

---

### Post by cmnorton on 2007-11-29
Here are some references:

[http://www.linuxforums.org/forum/servers/41668-mysql-problems-_-solved-_.html](http://www.linuxforums.org/forum/servers/41668-mysql-problems-_-solved-_.html)
[http://forums.mysql.com/read.php?11,9689,9689](http://forums.mysql.com/read.php?11,9689,9689)
[http://rpbouman.blogspot.com/2006/01/installing-mysql-50-from-rpm-on-ubuntu_07.html](http://rpbouman.blogspot.com/2006/01/installing-mysql-50-from-rpm-on-ubuntu_07.html)

---

### Post by Diabolis on 2008-04-15
I had the same problem. What was wrong in my system was that I had installed **mysql-server** and **mysql-server-5.0**, so I removed the first which I suppose is an older version.

---

### Post by Athelstan101 on 2008-04-15
You could try running the following to connect to the server (assuming that it's on the localhost):
```
$ mysql -u root -h 127.0.0.1 mysql -p
```

This will show you whether or not the package is installed:
```
$ dpkg -S mysql-server
```

---

