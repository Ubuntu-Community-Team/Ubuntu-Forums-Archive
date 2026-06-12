---
title: "HOW TO: Local installation of wordpress on gutsy gibbon (with LAMP)"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by boirax on 2008-04-12
Hello,

So you want to tinker with your Wordpress blog before releasing it to the world, experiment with themes or pages ... and you want to do it on your Ubuntu computer.  Here is how I managed to make a local install of my Wordpress on Ubuntu 7.10 - the Gutsy Gibbon -.  I followed a number of threads, posts and bloggs.... and a bit from each made it work in the end.  Here's a combination of copy-paste and reorganization to display it in a self-contained "how to".
I'm pretty much an Ubuntu beginner, so if anything is wrong or inaccurate feel free to comment on it.


We will do this in two steps:

1.  Install LAMP and test it.  (Wordpress needs a server, a database, etc... so we have to install those tools)
2.  Install Wordpress and do the initial configuration


<<<<<<<<<<<<< 1.  INSTAL THE SERVER STUFF >>>>>>>>>>>>>>>>>

First I did a Lamp installation (in this case, Linux, Apache, MySQL and PHP).

<<< APACHE >>>

Install Apache typing the following command on the terminal,
```

sudo apt-get install apache2

```
And to see if it worked, type [http://localhost](http://localhost) on your web-browser of choice.  You should
see this result:

[IMG]http://69.89.31.201:2082/viewer/home%2fzenitdel%2fpublic_ftp/apache_works.png[/IMG]


<<< PHP >>>

Now install PHP with,
```

 sudo apt-get install php5 libapache2-mod-php5

```

You can also check which version of PHP you have installed with,
```

php -v

```

We now stop and restart apache,
```

sudo /etc/init.d/apache2 restart

```

I get this error,

> Could not reliably determine the server's fully qualified domain name,
using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name,
using 127.0.1.1 for ServerName

If you are going to use a local install, going to
[http://localhost](http://localhost)
should be sufficent.  If you still want to get rid of the error, type in the terminal,

```
sudo gedit /etc/apache2/httpd.conf
```

add the line:
*ServerName "localhost"*

save the file.


then in terminal:
```
sudo /etc/init.d/apache2 restart
```


Note that you can also use,
ServerName "YourSite.com" 
on the httpd.conf file if you prefer.


Let's check if PHP worked.  For that create a simple php file

```

sudo gedit /var/www/testphp.php

```

containing this text,

<?php
phpinfo();
?>


save, exit, and point your web-browser to, [http://localhost/testphp.php](http://localhost/testphp.php)

If it worked (you got a long list with all your configuration details on your browser) then delete the file for security.

```

rm  /var/www/testphp.php

```


<<<< MYSQL (with PHP5)>>>>
```

sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql

```

It might be that during the install, MYSQL asks for you to provide a password.
Write it down, because you'll need it later on.  Let's say you chose 'mycheekypwd'

If you want to make MySQL accessible to people outside your computer you may have to edit,
/etc/mysql/my.cnf, and comment out 'bind-address = 127.0.0.1' or add your own IP address. 
(for more see here) [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


To make things easier you may want to use the package mysql-admin, so get it as,
```

sudo apt-get install mysql-admin

```
(note that you need the Universe repository enabled for that)

Ok, now time to setup your MySQL password.

If you were prompted above, then when you follow some common instructions to do,
```

mysql -u root

```
You will get the error,
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
which means, ... you think mysql has no password for root, but it does, because you set it earlier.  So you should instead type,
```

mysql -u root -p

```
which means, ... you want to access mysql and you want a prompt to ask you for your "-p" password.  So you enter "mycheekypwd"
and should get,

    Welcome to the MySQL monitor.  Commands end with ; or \g.
    Your MySQL connection id is 14
    Server version: 5.0.45-Debian_1ubuntu3.3-log Debian etch distribution

    Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

    mysql>


if you changed your mind concerning your password, you can change it with,
```

 SET PASSWORD FOR 'root'@'localhost'= PASSWORD('mycunningpassword');

```

REMEMBER:  in mysql, commands must end with a semicolon ' ; '
and a successful output will be,
Query OK, 0 rows affected (0.00 sec)

<<<<<<<<<<<<< 2.  INSTALLING WORDPRESS >>>>>>>>>>>>>>>>>

Ok!!! on to the second part.  While still on the MYSQL command line, create a database (name it 'wordpress' or whatever you wish)


<<< preparing the MYSQL database >>>

```

mysql>  CREATE DATABASE wordpress;

```
should output,  'Query OK, 1 row affected (0.05 sec)'
create user and give it a password,
```

mysql> CREATE USER memyself;

```
memyself is a username you choose, of course
```

mysql> SET PASSWORD FOR memyself = PASSWORD("hardtobreakpwd");

```
(the password hardtobreakpwd goes within the quotation marks and is your own, obviously) and give yourself rights
```

mysql>GRANT ALL ON wordpress.* TO memyself IDENTIFIED BY 'hardtobreakpwd';

```

and type exit to quit the mysql command line.

<<< installing wordpress >>>

download the latest tar, at
[http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz)

and save it to your home folder, then do,
```

 sudo tar -zxvf wordpress-2.5.tar.gz --directory=/var/www/

```

Now make a copy of the configuration file
```

sudo cp /var/www/wordpress/wp-config-sample.php /var/www/wordpress/wp-config.php

```

and edit,

```
 sudo gedit /var/www/wordpress/wp-config.php
```

changing

    // ** MySQL settings ** //
    define('DB_NAME', 'putyourdbnamehere');    // The name of the database
    define('DB_USER', 'usernamehere');     // Your MySQL username
    define('DB_PASSWORD', 'yourpasswordhere'); // ...and password
    define('DB_HOST', 'localhost');    // 99% chance you won't need to change this value
    define('DB_CHARSET', 'utf8');
    define('DB_COLLATE', '');


to the equivalent


    // ** MySQL settings ** //
    define('DB_NAME', 'wordpress');    // The name of the database
    define('DB_USER', 'memyself');     // Your MySQL username
    define('DB_PASSWORD', 'hardtobreakpwd'); // ...and password
    define('DB_HOST', 'localhost');    // 99% chance you won't need to change this value
    define('DB_CHARSET', 'utf8');
    define('DB_COLLATE', '');



with your parameters.  check spelling, save and close.

Now go to,

[http://localhost/wordpress](http://localhost/wordpress)

and you should be greeted by the wordpress configuration page.
Done!

I hope this helps others to achieve a smooth install.
Have fun blogging!

---

