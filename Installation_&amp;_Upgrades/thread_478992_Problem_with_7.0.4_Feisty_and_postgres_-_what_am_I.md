---
title: "Problem with 7.0.4 Feisty and postgres - what am I misisng?"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by swift99 on 2007-06-19
I am setting up a combined LAMP / Ruby+Apache+Mongrel+Postgres server (LAMP RAMP, I guess) using Feisty Fawn Server.

Specifically, [https://wiki.ubuntu.com/7.04Tour#head-84963104dee2d38a5347a14a83aa0281b5def5e6]("https://wiki.ubuntu.com/7.04Tour#head-84963104dee2d38a5347a14a83aa0281b5def5e6") states that "For those using PostgreSQL or MySQL, **7.04 includes PostgreSQL 8.2** and MySQL 5.0.38"  (emphasis added).  However, I am not finding postgres either (a) installed or (b) available for install.

I built my CD from the downloaded ISO and installed with no problems.  I chose the LAMP installation because one of the packages I need to run on the server uses MySQL.  However, my own software uses Postgresql.

I have found packages that reference PostGreSQL, but have not found postgresql itself.  While I could install postgresql manually, I would prefer to use apt-get/synaptic if possible.

What am I missing?

Thanks in advance.

---

### Post by angryfirelord on 2007-06-19
```
sudo apt-get install postgresql-8.2
```

---

### Post by swift99 on 2007-06-19
Sigh!  If only it were always this easy ...  That was it!

:redface:  Thanks!

---

### Post by angryfirelord on 2007-06-20
Haha np. If you can't seem to find a package, doing an **apt-cache search *name_of_thing*** should help you a little bit.

---

