---
title: "install LAMP in Ubuntu 10.10"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by caje.c on 2010-12-02
Hi, 
 
i'm starting to use Ubuntu and i install in a machine the ubuntu 10.10. Now i'm trying to install some software in the OS (the PHP5, Apache, etc), but i'm having some problems.
 
This forum have some threads explaining how to install in with a server cd, but i don't have this cd. Where can i get it? Can i install now the software? There is some site to download the apache? What's the steps that i have to do to install the software?
 
Thanks, in advance, for the help, apologizing for the ignorance, but as i said, i'm starting my use on Linux.

---

### Post by snowpine on 2010-12-02
Welcome to the forums!

Here is an easy-to-follow guide to configuring an Ubuntu server (including LAMP):

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

The short answer to your question is that, if you are connected to the Web, you can easily install any application from the Ubuntu repository using commands such as:

```
sudo apt-get install apache2
```

---

### Post by crichard on 2010-12-02
Try this to install LAMP Server in Ubuntu [http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/](http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/)

---

### Post by gdonwallace on 2010-12-02
Something else You might want to look at is Full Circle Magazine.  It is a Ubuntu based free pdf magazine.  A few issues back they did a full write up on how to setup a LAMP server.

---

### Post by Sakrecoer on 2011-02-08
I think this procedure is very good:
[http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/](http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/)

---

### Post by Sakrecoer on 2011-02-09
In that procedure, the tutor advises to create a folder called public_html and allow PHP in your home folder.

I'm not sure this is such a good idea on ubuntu since (as he writes himself) it is a depreciated way of things in security terms.

Would it be advisable to set permission on /var/www/ to 777*, using 

```
chmod -R 777 /var/www/
```

instead of changing the settings in /etc/apache2/mods-available/php5.conf
??

greatfull for an answer,
reSet Sakrecoer

---

