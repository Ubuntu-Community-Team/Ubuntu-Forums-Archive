---
title: "Can't login to phpmyadmin"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by jjsanders on 2009-12-02
Hello everyone,

I have problems with phpmyadmin on my machine. I am using ubuntu 9.04.
Installed mysql and phpmyadmin. With mysql i am able to login via command line using mysql -uroot -p<empty>.
But with phpmyadmin i get all the time access denied. [http://www.sanders-albek.nl/pics/Screenshot.png]("http://www.sanders-albek.nl/pics/Screenshot.png")
I installed it using apt-get install phpmyadmin and left everything default.

But i still get al the time access denied. 

This is how my config.inc.php file looks like
[http://www.codedump.be/code/441/](http://www.codedump.be/code/441/)

Can someone help me out?

---

### Post by DJ Scribblinni on 2009-12-02
By default phpmyadmin prevents the use of a blank password for logging in.  Change the password in mysql and you should be dandy.  It's recommended to change the password anyways for security reasons and best practice.  The command for such:
```
$ mysqladmin -u root password NEWPASSWORD
```

---

