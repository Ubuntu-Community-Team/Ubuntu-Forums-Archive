---
title: "execute command on ubuntu start"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by svecpetr on 2009-11-27
hi, I need run command for my server start when ubuntu starts (not at user login)

I need SUDO rights!

could you help me, where to paste this command
/usr/local/share/mysqlard/mysqlard.server start

please

---

### Post by aysiu on 2009-11-29
I think the root-executed startup scripts are in /etc/init.d/

You could perhaps symlink that command there?

---

### Post by svecpetr on 2009-11-29
yep, you are right

but /etc/init.d is directory with many files ... usually one file per service (it about 3 kB of code)

and finally for existing any file with init.d you must have another file in /etc/r0-6.d/
that about next 3kB of code

... if some body helps me, how crete this files, I can add new service with rc_update.d

hey, I need execute only one command /usr/local/share/mysqlard/mysqlard.server start :o)

---

