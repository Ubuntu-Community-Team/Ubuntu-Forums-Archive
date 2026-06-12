---
title: "Updated Ubuntu 8.04.01, now PHP pages not working"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by johnnyb123 on 2012-12-07
I just updated my Ubuntu 8.04.1 system using Webmin (showed 16 updates ready).  Immediately after the updates were applied, the websites with PHP pages stopped working properly.  i.e. each time the site accessed a .php page, the browser would download it, rather than display it.  My html pages worked fine.

I began searching through the forums for help and found a thread that suggested running the command sudo a2enmod php5.  It appeared to run ok but when I restarted apache, it would not restart and I get the following error:

* Restarting web server apache2
apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory
   ...fail!

Now none of my websites are working because Apache won't restart.  Please help!  I am not an experienced Ubuntu guy and am a bit frantic to restore my websites.  Thank you!!

---

### Post by mastablasta on 2012-12-07
did you check apache2.conf
 
apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load
 
it says there is a syntacs error in that file.

---

### Post by SlugSlug on 2012-12-07
You should really upgrade to new LTS

but if your able to install via your repos try this

[http://linuxhostingsupport.net/blog/ubuntu-php-libphp5-so-missing-cannot-open-shared-object-file](http://linuxhostingsupport.net/blog/ubuntu-php-libphp5-so-missing-cannot-open-shared-object-file)

---

### Post by johnnyb123 on 2012-12-07
> **SlugSlug said:**
> You should really upgrade to new LTS

but if your able to install via your repos try this

[http://linuxhostingsupport.net/blog/ubuntu-php-libphp5-so-missing-cannot-open-shared-object-file](http://linuxhostingsupport.net/blog/ubuntu-php-libphp5-so-missing-cannot-open-shared-object-file)
I owe you a big THANK YOU, SlugSlug!  The link that you provided FIXED the problem and I'm back up and running.  Even the php pages are functioning properly again. 

I will start investigating the steps to upgrade to the new LTS, as you recommended.
Thank you again!

---

### Post by SlugSlug on 2012-12-07
no prob :)

---

### Post by Androzani1 on 2012-12-07
Before upgrading to 12.04, I would recommend running it in a Live CD just to check all of the hardware works. You may need to downgrade to Xubuntu if the hardware no longer works.

---

