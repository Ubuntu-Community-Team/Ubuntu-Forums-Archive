---
title: "firefox embedded php"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by oradano on 2010-07-16
I'm new to LAMP and PHP, please bear with...

I'm writing smple html pages with embedded php <?php   ?> and the php isn't executing, no output to screen.  I've added plain text outside the php tags to confirm.

I've got apache httpd.conf configured with AddType's for php.  Any other suggestions?

---

### Post by dapperdanny77 on 2010-07-16
check if you have installed the php module
> dpkg -l libapache2-mod-php5

then check your apache config if the module is being loaded

you can make a small php to test your installation

<?php
phpinfo()
?>

---

### Post by oradano on 2010-07-16
> **dapperdanny77 said:**
> check if you have installed the php module
> dpkg -l libapache2-mod-php5

then check your apache config if the module is being loaded

you can make a small php to test your installation

<?php
phpinfo()
?>


thanks again for  your reply, fun being a newbie, I actually have phpmyadmin installed and working no problem so I knew it was something really obvious

I've been is trying to embed php code inside index.**[COLOR=Black]html[/COLOR]**, it's the other way 'round, index.**php** can have html tags inside it, I tried with index.php and it's good

---

