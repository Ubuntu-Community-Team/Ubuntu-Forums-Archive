---
title: "MySQL Error"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by dgcarter on 2007-08-10
I'm having issues with MySQL... I have installed Ubuntu Dapper LAMP Server and after installation MySQL works, then I setup my Hosts file and networking etc... and after I restart I get this:

```
root@mail:~# mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)
root@mail:~#

```

I have re-installed 3 times already, and been up and down google and I have yet to find an answer, can anyone help?

---

### Post by darkmediator on 2007-08-10
Edit ur "/etc/hosts" file and put an entry "127.0.0.1  localhost" in it and then try

1. sudo echo "127.0.0.1  localhost" >> /etc/hosts
2. sudo /etc/init.d/mysql restart
3. then try!

---

### Post by dgcarter on 2007-08-10
thanks, but unfortunately I'm still getting the same error...

---

### Post by darkmediator on 2007-08-11
Post the contents of /etc/hosts

---

