---
title: "XAMPP PHP and Mysql commandline problem"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by gsip on 2009-11-26
Hi guys,

I installed XAMPP 1.7.2. on Ubuntu 9.10. I know you can install the standard LAMP, but that does not include all the precompiled plugins from XAMPP.

XAMPP installs and starts with /opt/lampp/lampp start and [http://localhost](http://localhost) works. But my problem is that when I want to use MySQL or PHP in the terminal i get :

"The program 'php' is currently not installed.  You can install it by typing:
apt-get install php5-cli"

So how can I get PHP and MySQL from XAMPP running in the terminal? Or even better get Ubuntu to regocnize that PHP and MySQL are installed...

Thanks!

---

### Post by DominaDoom on 2009-12-05
Try the separate installations.

If there is a patch to this problem, I do not know it.

---

### Post by lehmanshaunc on 2012-12-10
I ran into a very similar problem when trying to build a Symfony bundle on Ubuntu 12.04 using lammp. 

The Symfony command asked me to type the following from the terminal:
$ php app/console generate:bundle ...

I had to change the command to the following in order to make it work
/opt/lampp/bin/php app/console generate:bundle ...
 
I hope this helps.

---

### Post by oldos2er on 2012-12-10
Old thread closed, please don't bump old threads.

---

