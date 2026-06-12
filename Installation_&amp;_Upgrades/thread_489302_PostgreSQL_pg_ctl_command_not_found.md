---
title: "PostgreSQL: pg_ctl command not found"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by garyvdm on 2007-07-01
Hi

I have installed PostgreSQL 8.2 on kubuntu edgy. I want to restart PostgreSQL, but when I type in pg_ctl in the console, I get :
```
garyvdm@beta:/$ pg_ctl reload
bash: pg_ctl: command not found
```

Is there something wrong with the way I have installed PostgreSQL? What can I do to get this to work?

Gary

---

### Post by garyvdm on 2007-07-02
Someone helped me on IRC. On Ubuntu, instead of pg_ctl, you  need to use /etc/init.d/postgresql-?.? where ?.? is the version installed.

---

### Post by Migou on 2007-08-27
The command pg_sql should be in a directory such as
/usr/lib/postgresql/8.2/bin/
(for postgresql 8.2 :-))

You can call it by using the absolute path :
/usr/lib/postgresql/8.2/bin/pg_ctl  options

or you can modify the .bashrc, adding /usr/lib/postgresql/8.2/bin to the PATH variable

---

### Post by +mw.MetalGear on 2008-03-06
i have same problem i have install ununtu 7.10 SE and 

 PostgreSQL 8.2

i go to /usr/lib/postgresql/8.2/bin/ an execute the command  pg_sql  byt it show me same error
can someone tell me how is corect

---

