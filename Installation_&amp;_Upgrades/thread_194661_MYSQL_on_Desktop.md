---
title: "MYSQL on Desktop"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by vasimakhtar on 2006-06-11
Hi,
I want to install Mysql on my desktop and use it as a server to learn about database and mysql. How can I configure the same without installing server edition.
Thanks.

---

### Post by nanotube on 2006-06-11
yea, just install the mysql packages from the repositories. it doesn't matter that you are running a desktop.

---

### Post by vasimakhtar on 2006-06-11
Thanks.I have installed Mysql Administrator and Query browser. Do I have to install more? Is there any default database to connect or I have to create one? How can I start connection?
thanks.

---

### Post by nanotube on 2006-06-12
[QUOTE=vasimakhtar]Thanks.I have installed Mysql Administrator and Query browser. Do I have to install more? Is there any default database to connect or I have to create one? How can I start connection?
thanks.[/QUOTE]
that's mysql-specific, and i haven't played with mysql in a while, so can't tell you any specifics about mysql syntax. look around for mysql howtos on the web to find things, or maybe there is a howto on these forums...

---

### Post by markthetech on 2006-06-17
I just tried to setup MySQL administrator and got this error. Please Help:confused: 

E: mythtv-database: subprocess post-installation script returned error exit status 1
E: mythtv: dependency problems - leaving unconfigured

---

### Post by randlieb on 2006-06-18
this may be a bit off topic but i have installed mysql admin in Dapper. set the password, open the app, can click on all sections until i try "user admin" which freezes and have to force quit to get out. any advice or point to another thread if anybody has seen this.
thanks

---

### Post by jaredvolkl on 2006-07-14
> **randlieb said:**
> this may be a bit off topic but i have installed mysql admin in Dapper. set the password, open the app, can click on all sections until i try "user admin" which freezes and have to force quit to get out. any advice or point to another thread if anybody has seen this.
thanks
I also found this happening. Turns out there is a workaround.

run this:
```
export DEBUG_DONT_SPAWN_FETCHES=1
```

and then you can start mysql-admin from the command line. Alternatively, you can add the export line to your .bashrc or .bash_profile to have it run all the time.

---

### Post by slider on 2006-07-14
If you want to play around with MySQL, I suggest installing phpmyadmin. Configuration is a snap, just read the instructions and it allows you to graphically browse, create and modify databases.

---

### Post by az on 2006-07-14
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by jaredvolkl on 2006-07-14
> **slider said:**
> If you want to play around with MySQL, I suggest installing phpmyadmin. Configuration is a snap, just read the instructions and it allows you to graphically browse, create and modify databases.I agree, phpmyadmin is great, unless you're importing large .sql files, then you'll have to use the command line.

May I also suggest [turbodbadmin]("http://www.turboajax.com/turbodbadmin/"). More or less, it's phpmyadmin injected with a healthy dose of Web 2.0. The last time I tried it, it was only at a 0.1 release and it was pretty bare on features. I see a 0.2 release is out now though.

I'd still use phpmyadmin for any critical apps but turbodbadmin could be fun to play around in.

---

