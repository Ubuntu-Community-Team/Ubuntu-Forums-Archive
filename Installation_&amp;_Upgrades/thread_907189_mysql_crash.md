---
title: "mysql crash"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by herrbrand on 2008-09-01
hello

I installd mysql good but when i try to start mysqld_safe --user=mysql it gives to lines of text and then only the cursos keeps blinking.
I can typ commands but nothing happens.
I have to restart the server to work forther.

how can i solve this?

Robbert

---

### Post by manishtech on 2008-09-02
Use this command to manage the server


Start:

```
sudo /etc/init.d/mysql start
```

Stop
```
sudo /etc/init.d/mysql stop
```

Restart

```
sudo /etc/init.d/mysql restart
```

---

### Post by manishtech on 2008-09-02
Now if you want to login to mysql frontend, type this

```
mysql -u root -p
```

and then enter the root password which you created while installing mysql

I suggest you not to work much on root, create another user and then use it. In that case the command would become

```
mysql -u newuser -p
```

---

