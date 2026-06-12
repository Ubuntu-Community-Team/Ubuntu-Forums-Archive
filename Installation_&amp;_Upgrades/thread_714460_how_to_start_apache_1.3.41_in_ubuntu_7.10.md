---
title: "how to start apache 1.3.41 in ubuntu 7.10"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by fiza11 on 2008-03-03
I want to run apache 1.3.41 on ubuntu 7.10

I installed it but apache was not able to start giving me bad command
I tried to reinstall it but this time while running ./configure file it didn't created the make file to run giving a syntax error.

Can anyone help me please as I need this server running by tommorrow

---

### Post by jpeddicord on 2008-03-03
You shouldn't have to build from source at all.

```
sudo apt-get install apache2
```

That will set up a default server on port 80 in /var/www and start the service automatically each boot.

If for some reason you'd rather build from source, could you post the error messages you are receiving?

---

### Post by fiza11 on 2008-03-04
It gives an error saying couldn't find package apache 2

---

### Post by fiza11 on 2008-03-04
If I try to start apachectl it show  that httpd couldn't be started

---

