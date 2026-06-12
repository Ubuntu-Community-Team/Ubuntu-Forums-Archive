---
title: "How to get the password for the the user created after installing postgresql.."
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by shredder12 on 2008-10-27
I was installing a software which required postgresql database so i downloaded and installed it using synaptic..and while installing the software i was asked to execute a command which required authentication of the postgres user..
How do i know the password of the user created which was created while installing postgresql...?
Somebody help please..i m really confused...

---

### Post by lemming465 on 2008-10-28
Probably the unix level password for the postgres user isn't set.  (sudo grep postgres /etc/shadow will start off "postgres:!!:").  If you need to do things as user postgres you can simulate a login to a shell running as user postgres by "sudo -i -u postgres".

---

