---
title: "/var/www/html/index"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by andy109 on 2014-12-09
I know how to install joomla on the root on  Ubuntu server 12  because it use /var/www 
but Ubuntu 14.1 I am a little bit confused
how do I install Ubuntu on the root on Ubuntu 14.1 
I don't want [http://mysite/joomla](http://mysite/joomla) I want [http://joomla](http://joomla)
howdo I do this thanks

---

### Post by newbie-user on 2014-12-10
You need to edit the 000-default.conf file in /etc/apache2/sites-available.

For the document root, change it from /var/www/html to /var/www/joomla

Then restart apache

---

### Post by andy109 on 2014-12-13
Thanks. What I did was extracted all joomla.zip into /var/www/ so it look so messy in there then I edit /etc/apache2/apache.conf then change DirectroryPath to /var/www
it works but two thing is my concern
1. I chown /var/www to www-data:www-data then use chmod 755 to /var/www is this ok?
2. i didnt create folder in /var/www if i did that the apache wouldn't read it? or should i tell DirectoryPath to /var/www/joomla?

If I want to create virtual webserver where do i keep all folder and which files need to be configure?

thanks

---

### Post by newbie-user on 2014-12-15
> **andy109 said:**
> Thanks. What I did was extracted all joomla.zip into /var/www/ so it look so messy in there then I edit /etc/apache2/apache.conf then change DirectroryPath to /var/www
it works but two thing is my concern
1. I chown /var/www to www-data:www-data then use chmod 755 to /var/www is this ok?
2. i didnt create folder in /var/www if i did that the apache wouldn't read it? or should i tell DirectoryPath to /var/www/joomla?

If I want to create virtual webserver where do i keep all folder and which files need to be configure?

thanks

1. Usually you want the permissions to be 644, as you don't want things to be executable by everyone.
2. If doesn't matter where you create the folder. You just need to tell apache where the Document Root is. This is done within /etc/apache2/sites-available folder, where you list all the websites that apache is responsible for.

---

