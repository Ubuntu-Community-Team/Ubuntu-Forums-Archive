---
title: "Phpmyadmin problem"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by svance1947 on 2010-11-10
Installed LAMP server on 10.4
Installed phpmyadmin.

When I call /localhost/phpmyadmin, I get the login page.
I enter root and the password entered during install.

At that point, I get a pop-up window saying I'm trying to open index.php and asking what I should do with the file.

I've removed everything and started over, to no avail.

Any suggestions?

---

### Post by jbruced on 2010-11-10
When you type 

127.0.0.1

in the address bar, does it say "It works!"?

This is the test to make sure apache is running correctly.

---

### Post by svance1947 on 2010-11-10
>When you type 127.0.0.1
>in the address bar, does it say "It works!"?

Yes... Apache2 is working fine.

Hmmm... can't find php.ini
The install didn't create one under /php5/apache2/

---

### Post by lmarmisa on 2010-11-10
Try to create a file named info.php in the /var/www folder with this content:

```

<?php
phpinfo();
?>

```

Then type this URL in your browser: [http://localhost/info.php](http://localhost/info.php)

---

### Post by jbruced on 2010-11-10
I used these instructions 3 times, no problems.



[http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/]("http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/")

---

### Post by lisati on 2010-11-10
> **svance1947 said:**
> Installed LAMP server on 10.4
Installed phpmyadmin.

When I call /localhost/phpmyadmin, I get the login page.
I enter root and the password entered during install.

[COLOR="Red"]At that point, I get a pop-up window saying I'm trying to open index.php and asking what I should do with the file.[/COLOR]

I've removed everything and started over, to no avail.

Any suggestions?

Try clearing your browser cache. There are one or two other things you might want to check here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

---

### Post by svance1947 on 2010-11-10
lmarmisa

Not recognizing info.php
Asking what to do with file

I installed the LAMP server from within synaptic.

thanks

---

### Post by lmarmisa on 2010-11-10
You had some problem installing php.

Try to reinstall the LAMP server using the package "tasksel".

Install tasksel with synaptic and then type this command

> 
sudo tasksel



[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by svance1947 on 2010-11-11
The solution had nothing to do with phpmyadmin.  It was a firefox problem. Once I cleared the firefox cache and cleaned up cookies, etc... everything worked fine.
 
It seems that firefox was not getting the file definition that it needed to properly recognize the file.  Mozilla's support site has the details.

---

