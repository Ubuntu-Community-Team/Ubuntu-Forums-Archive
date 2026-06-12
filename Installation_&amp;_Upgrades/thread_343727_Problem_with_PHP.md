---
title: "Problem with PHP"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by KombOver on 2007-01-21
I have tried all of the suggestions in the LAMP how-to guide.  MySQL 5 runs fine,  Tomcat5 runs fine, Apache2 runs fine, but whenever I type a url for an *.php page (/http://localhost/phpinfo.php, for example) a Firefox dialog displays telling me I am trying to open a php script and asks what do I want to do with it?

I have tried 
- apt-getting installing both versions of php (4 and 5), including the (libapache2-mod-php4), and apache2 restarts,

- adding the following to the apache2 conf file
AddType application/x-httpd-php5 .php5

I know that apache is finding the .php files since if I open them it displays the source.

It looks as if Apache2 doesn't know that php is install.

Also note that [http://127.0.1.1/phpmyadmin](http://127.0.1.1/phpmyadmin) does not work either even though:

 sudo a2enmod php5
This module is already enabled!

I've spent two hours on this and it is probably somewhere in the vast forum, but I cannot locate the specific solution.

FYI, this is my first post and I have already installed a great number of apps.  This is truly a great community!

---

### Post by RobNY on 2007-01-22
> **KombOver said:**
> 
- adding the following to the apache2 conf file
AddType application/x-httpd-php5 .php5


This will cause apache to only parse files ending in ".php5".   You shouldn't have needed to add this anyway as under apache2, these definitions are described by the configuration files for modules.  

Make sure you have the file:  /etc/apache2/mods-enabled/php5.conf  which should contain the lines:

  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps

Also, check for the existence of /etc/apache2/mods-enabled/php5.load which will contain the LoadModule directive.

If you do not have php5.conf (or .load), I suspect something went wrong with your installation of apache2 or php5.

---

### Post by KombOver on 2007-01-22
Thanks for your help.  Both confs exist and contain what is expected.  Upon further investigation, I found that according to Apache, this is a known issue,

[http://wiki.apache.org/tomcat/UsingPhp]("http://wiki.apache.org/tomcat/UsingPhp")

Php5 isn't compatible - it lacks the necessary servlet code.  I would need to drop back to php4, install a patch to the source, reconfig and then re-make.  Way too much hassle, I'll just stick to servlets and jsp.  

I am sure that eventually php and tomcat will work more seamlessly.  I will watch the two communities periodically.

---

