---
title: "problem running php projects in lamp server"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by alex_grg on 2011-06-21
i just installed lamp server, got phpmyadmin working, then i copied a site folder to /var/www/ using nautilus and tried to run the site with [http://localhost/sitefolder/index.php](http://localhost/sitefolder/index.php) in browser and it showed blank. then i checked database connection, performed some queries and it is working, simpliy i can't get my page running. that site worked perfectly fine in wamp server, plz help me

---

### Post by mörgæs on 2011-06-21
If you want help, you must give us a foundation for helping, that is a detailed description of what you have done to isolate and/or solve the problem. 

Let's forget the database and focus only on Apache and PHP. To begin with, have you checked all file permissions? Can you create a new PHP file and make it show in the browser?

---

### Post by alex_grg on 2011-06-21
yeah it just works fine

---

### Post by alex_grg on 2011-06-21
i can create a simple php file with some message, and the browser displays fine

---

### Post by SeijiSensei on 2011-06-21
Look at /var/log/apache2/error.log?  What does it report?

My guess is that either there's a PHP syntax error somewhere or the MySQL connection isn't working properly.

If you'd prefer to have the application [display errors in the browser]("http://www.php.net/manual/en/errorfunc.configuration.php#ini.error-reporting"), you can add

```
ini_set("display_errors","1");
```

to the top of your script.  Just remember to turn it off for production.

---

### Post by alex_grg on 2011-06-21
ok i put that code and still nothing changed, also there is no error in /var/log/apache2/error.log

---

### Post by alex_grg on 2011-06-21
starting all over again i just copied a fresh copy of site folder again inside /var/www/ and tried to run localhost/sitefolder/index.php it gave 403 error

Forbidden 

You don't have permission to access /sitefolder/index.php on this server.
  Apache/2.2.17 (Ubuntu) Server at localhost Port 80

---

### Post by arrrghhh on 2011-06-21
> **alex_grg said:**
> starting all over again i just copied a fresh copy of site folder again inside /var/www/ and tried to run localhost/sitefolder/index.php it gave 403 error

Forbidden 

You don't have permission to access /sitefolder/index.php on this server.
  Apache/2.2.17 (Ubuntu) Server at localhost Port 80

Please don't [crosspost](http://ubuntuforums.org/showthread.php?t=1787684) - especially creating a new thread again, that's pretty rude dude.

You seemed to be getting plenty of help here, no need to create another thread in the Server section, which doesn't even seem to apply to your setup.

---

### Post by mörgæs on 2011-06-21
> **mörgæs said:**
> ... have you checked all file permissions?

The manual in my signature explains how to.

---

### Post by alex_grg on 2011-06-21
ok em sorry. that won't happen again,

---

