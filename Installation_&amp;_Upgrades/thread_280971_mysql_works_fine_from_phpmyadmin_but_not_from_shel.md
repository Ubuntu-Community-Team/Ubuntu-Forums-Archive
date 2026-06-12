---
title: "mysql works fine from phpmyadmin but not from shell"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by bld on 2006-10-20
I have installed Ubuntu 6.06 on clean computer doing all according to instructions from [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06).

I have problem with mysql. I can do everything from phpMyAdmin (login, create users, databases etc). But when I try do anything from shell (no matter on root or normal user account) I got still an error

eg. when I try to "mysqladmin version" i got:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

of course when try login on mysql user 'root'. With different users the same effect.

Any help ?

Best regards,
Przemek

---

### Post by bld on 2006-10-20
Problem solved. I was using bad mysql commands syntax. Sorry...

---

### Post by ojasvi rajpal on 2006-10-20
can u guide me on how to install mysql ? on ubuntu 6.06

---

