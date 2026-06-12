---
title: "phpmyadmin eror"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by ssinghi on 2007-05-01
I installed phpmyadmin, LAMP and everything using apt-get but i get the error: 

#1045 - Access denied for user 'www-data'@'localhost' (using password: YES)

any clue, whats happening and what do I need to do?

Thanks!

---

### Post by mvaniersel on 2007-05-01
Well, this means you were trying to get access to a mysql database as user www-data (this usually means you do it through the webserver) with an invalid password.

But you forgot to mention what you actually did before you got that error. What command did you type, or what address did you visit?

IIRC mysql is set up out-of-the-box with a user "root" with no password.

---

### Post by ssinghi on 2007-05-02
Sorry, I was too brief in my original message.  I was trying to login to phpmyadmin from the url:
[http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php) 

as root with blank password, and i get that error "#1045 - Access denied for user 'www-data'@'localhost' (using password: YES)". 

I am able to login into mysql from console, using 'mysql -u root'.

Thanks!

---

### Post by Simpele on 2007-05-02
I had the same problem, even after setting a password for root.
I removed cookies. Then I purged phpmyadmin through Adept to reinstall it afterwards. It solved the problem.

---

### Post by ssinghi on 2007-05-02
Thanks! I did 

sudo aptitude purge phpmyadmin

and then 

sudo aptitude install phpmyadmin

that fixed the problem. Earlier I had installed using apt-get.

---

