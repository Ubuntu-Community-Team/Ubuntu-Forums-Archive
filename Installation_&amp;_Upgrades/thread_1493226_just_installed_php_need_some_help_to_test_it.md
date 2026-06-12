---
title: "just installed php need some help to test it?"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by ulao on 2010-05-25
I see :

[notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch configured -- resuming normal operations

and 

sudo a2enmod php5
This module is already enabled!

reports ok. but I can not get my <?php phpinfo(); ?>   to work on my test page? Also my domain/test.hph or testphp.php does not work.

Whats a good place to start looking.

---

### Post by SlidingHorn on 2010-05-25
**Edit: *****Nevermind, can't upload a php file to the forum***


I'm not sure exactly what could be wrong due to the typos...please post the exact content and filename of your phpinfo file.

---

### Post by ulao on 2010-05-25
Well I guess I could have used a simple test. I can not even get this to work.

<?php echo("test");  ?>


Ok never mind I guess I'm dumb, it work if the file is name .php not .html, i did not think it had to be. Do I need to enable html to use php in a conf file?

ok found it

AddType application/x-httpd-php .html .htm

now it works.

---

