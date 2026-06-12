---
title: "LAMP Install and PHPinfo"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by Bartly on 2010-02-04
I installed LAMP using tasksel on a 9.10 desktop. Apache works but when I run phpinfo it just returns a page with the code < ? php phpinfo();  ?>. This is the second time I have installed LAMP using tasksel, and the first time everything worked perfectly, but on this install apparently php is not working. NOt sure where to start fixing this.

---

### Post by Bartly on 2010-02-04
Well, I just installed phpmyadmin and it does work, so not sure why test.php dos not.

---

### Post by Bartly on 2010-02-04
And wordpress works. However, I still need to run the phpinfo function, what am I doing wrong? I created the script and named it test.php and put it in the /var/www directory.

---

### Post by cwoggon on 2010-02-04
> **Bartly said:**
> I installed LAMP using tasksel on a 9.10 desktop. Apache works but when I run phpinfo it just returns a page with the code < ? php phpinfo(); ?>. This is the second time I have installed LAMP using tasksel, and the first time everything worked perfectly, but on this install apparently php is not working. NOt sure where to start fixing this.
 Try changing the code in your test.php file to this:
<?php
phpinfo();
?>

---

### Post by Bartly on 2010-02-04
> **cwoggon said:**
> Try changing the code in your test.php file to this:
<?php
phpinfo();
?>
 
That is how I wrote it in the script, although Firefox reads it in one line. However! I needed to check phpinfo to make sure that ldap was enabled. But I just got ldap authentication working for Wordpress, so everything is working, just not the phpinfo script. I am sure it must be a PIBCAK or ID10T error!
Thanks for your reply. 
 :popcorn:

---

### Post by cwoggon on 2010-02-04
> **Bartly said:**
> That is how I wrote it in the script, although Firefox reads it in one line. However! I needed to check phpinfo to make sure that ldap was enabled. But I just got ldap authentication working for Wordpress, so everything is working, just not the phpinfo script. I am sure it must be a PIBCAK or ID10T error!
Thanks for your reply. 
:popcorn:
 The fact that it is on line doesn't concerns me. What concerns me is the spacing you have before phpinfo();
 
There should only be whitespace (returns, spaces, tabs) around phpinfo();

---

