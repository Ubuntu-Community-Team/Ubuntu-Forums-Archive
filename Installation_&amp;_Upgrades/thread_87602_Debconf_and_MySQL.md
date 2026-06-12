---
title: "Debconf and MySQL"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by jrmann1999 on 2005-11-08
I've setup mysql to do replication between two machines.  One of them is my new ubuntu breezy server, and now debconf is spitting out a multitude of errors(presumably because the mysql database itself has changed and now the passwords aren't in sync).  How can I update the debconf password and/or reset it?

---

### Post by Stryker777 on 2006-01-18
vi /etc/mysql/debian.cnf

copy the password

Change the password in mysql to the one you copied

You answered your own question but for others sake I expounded.
Laterz

---

