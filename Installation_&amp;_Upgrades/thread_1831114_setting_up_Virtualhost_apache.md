---
title: "setting up Virtualhost apache"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by kingdm on 2011-08-22
Hello everyone.

I am setting up a VirtualHost on my Apache. I am quite not familiar with Ubuntu setup so I am wondering what will I do with the 000-default file (which contains a template of virtualhost syntax)? What filename will I save it to?

Thanks.

---

### Post by salemeni on 2011-08-23
> **kingdm said:**
> Hello everyone.

I am setting up a VirtualHost on my Apache. I am quite not familiar with Ubuntu setup so I am wondering what will I do with the 000-default file (which contains a template of virtualhost syntax)? What filename will I save it to?

Thanks.

```
#cd /etc/apache2/sites-available
$sudo cp 000-default site
$sudo nano /etc/apache2/sites-available/site


<VirtualHost *:80>
**ServerAdmin webmaster@test.com**
#
[B]DocumentRoot /var/www/
[/B]**ServerName www.test.com**
 ErrorLog ${APACHE_LOG_DIR}/error.log

      
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
$sudo ln -s /etc/apache2/sites-available/site /etc/apache2/sites-enabled
$sudo /etc/init.d/apache2 restart


```
test with browser [http://127.0.0.1](http://127.0.0.1)

---

