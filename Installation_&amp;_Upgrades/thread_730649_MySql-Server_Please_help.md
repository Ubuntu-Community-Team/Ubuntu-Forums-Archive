---
title: "MySql-Server Please help"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-03-21
I have installed MySql-server using Synpatic, but during the installation I wasn't asked to create a user/password.
My problem is now when I used Mysql administrator that I have also installed with synpaic
I need a user/password.
where is it MySql is installed under ubuntu ?
I mean where is the server ? dir ?
and how can i create a user/password. 
Thanks

---

### Post by alenis on 2008-03-21
you can create a user from the mysql client, as root, with the
create user <name>;
statement.
see [http://dev.mysql.com/doc/refman/5.0/en/create-user.html]("http://dev.mysql.com/doc/refman/5.0/en/create-user.html")
for details

---

