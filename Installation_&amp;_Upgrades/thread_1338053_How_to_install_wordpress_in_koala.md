---
title: "How to install wordpress in koala"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by rishabh_destiny on 2009-11-26
Hi
I have installed the LAMP server and mysql plus apache and all the things needed to run wordpress locally. However, i'm not able to run wordpress. I need urgent help.
Please

I used "tasksel" command at terminal and installed LAMP server

---

### Post by rudy.b on 2009-11-26
Can you explain the specific problem you're having running Wordpress?

---

### Post by rishabh_destiny on 2009-11-26
I did all these
> 

    * Home
    * About

Installing WordPress on Ubuntu

October 30, 2008

Install wordpress package:
$ sudo apt-get install wordpress

Enter in mysql prompt:
$ mysql -u root -p

Create a wordpress user:
mysql> grant all privileges on *.* to wordpress_user@localhost;

Set a password:
mysql> set password for wordpress_user@localhost = PASSWORD(‘yourpass’);

Create your database:
mysql> create database wordpress_mad;

Flush it:
mysql> flush privileges;

Add to /etc/apache2/apache2.conf :

# wordpress
Alias /blog /usr/share/wordpress
<Directory /usr/share/wordpress>
Options FollowSymLinks
AllowOverride Limit Options FileInfo
DirectoryIndex index.php
</Directory>

Remove wp-config.php link:
# rm /usr/share/wordpress/wp-config.php

Move config sample to original wp-config:
# mv /usr/share/wordpress/wp-config-sample.php /usr/share/wordpress/wp-config.php

After that, I edited /usr/share/wordpress/wp-config.php and replaced database variables with these ones I created.

And I now get DATABASE CONNECTION ERROR on localhost.

---

### Post by rudy.b on 2009-11-27
Going by that error message, I would verify that the mysql server is running and that the login credentials and database name are all set correctly in the wp-config.php.  And check that the mysql module is loaded for PHP.

---

### Post by rishabh_destiny on 2009-11-27
The wp-config.php settings
> // ** MySQL settings - You can get this info from your web host ** //

/** The name of the database for WordPress */

define('DB_NAME', 'putyourdbnamehere');



/** MySQL database username */

define('DB_USER', 'wordpress');



/** MySQL database password */

define('DB_PASSWORD', 'testing');



/** MySQL hostname */

define('DB_HOST', 'localhost');



/** Database Charset to use in creating database tables. */

define('DB_CHARSET', 'utf8');



/** The Database Collate type. Don't change this if in doubt. */

define('DB_COLLATE', '');

Database settings from terminal
> mysql> show databases
-> ;
+--------------------+
| Database |
+--------------------+
| information_schema |
| mysql |
| phpmyadmin |
| wordpress |
+--------------------+
4 rows in set (0.00 sec)

PS: I've created the database Wordpress using phpmyadmin. Althoug, I didn't gave any password at the time of creation (it didn't asked any, though), i've tried both ways editing the wordpress config file. First by wordpress as db name ans BLANK pass, and other time, wordpress as DB name, and "testing" as pass (which is my root pass for mysql on ubuntu)

Again, on opening 127.0.0.1---> IT WORKS!
on opening [127.0.0.1/wordpress] or [localhost/wordpress] --->> Error establishing database connection

---

### Post by rishabh_destiny on 2009-11-27
Ok. I;m successful in instlling and running Wordpress. But I'm having errors in installing themes. Whenver I try to install one,it gives some ftp kinda thing, which doesn't go further

---

### Post by rishabh_destiny on 2009-11-29
Bump

---

### Post by phillw on 2009-11-29
I don't run Wordpress - if you're using wordpress.org (not .com) there's a good thread with instructions over here --> [http://www.themelab.com/2008/03/02/how-to-install-a-wordpress-theme/](http://www.themelab.com/2008/03/02/how-to-install-a-wordpress-theme/)

Regards,

Phill.

---

### Post by rishabh_destiny on 2009-11-30
This is not for ubuntu. Installing wordpress locally on ubuntu is complete different thing. Please help, anybody

---

