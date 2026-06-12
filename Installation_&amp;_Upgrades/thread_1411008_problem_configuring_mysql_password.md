---
title: "problem configuring mysql password"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by mosty friedman on 2010-02-19
hey everyone,

I got this problem with configuring mysql root password, i am following these instructions here
[https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL)

the thing is when i type 

```

mysqladmin -u root password root

```

i get this error
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

any idea on how to fix this???

---

### Post by SecretCode on 2010-02-19
Your syntax is incorrect, to start with. You need _--password_ or _--password=_ or _-p_. And it's better practice not to give the password on the command line but to enter it afterwards. And I think you need to include a command keyword.
```
mysqladmin -u root --password status
Enter password:

```

---

