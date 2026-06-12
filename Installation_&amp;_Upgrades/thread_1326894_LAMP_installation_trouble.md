---
title: "LAMP installation trouble"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by Sherinnovation on 2009-11-14
I am trying to install LAMP in ubuntu
 For that
 I completed the following steps successfully in the order shown below
 
[LIST=1]
[*]*sudo apt-get install apache2*
[*]*sudo /etc/init.d/apache2 start*
[*]*sudo apt-get install php5     libapache2-mod-php5*
[*]*sudo /etc/init.d/apache2     restart*
[/LIST]
 After the above steps I created a PHP page named test.php in /var/www
 The contents of test.php is
 *<?php  *
 *echo “Hello World”;  *
 *?>*
 

 I am 100% sure that there is no syntactical errors in the php code.
 But when I access the page using *“[http://localhost/test.php](http://localhost/test.php)”, the following error showed*
 

 ***Parse error****: syntax error, unexpected T_STRING, expecting ',' or ';' in ****/var/www/test.php**** on line ****2***
 

  I don't know what to do at this situation. Please suggest me a solution.

---

