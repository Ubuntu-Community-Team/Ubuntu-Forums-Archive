---
title: "how to install horde on ubuntu edgy?"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2007-01-27
I run edgy with apache2 and now I installed horde, imp, gollem ...
But I didnt find any way how to access horde.

Horde is installed in /usr/share/horde3 but there is no reference to it in any apache2-config.
It seem installed but not "activated". Do I need to setup apache2.conf manually or put a config in conf.d or did I miss something?

How is it supposed to work?

thnx,

---

### Post by trac on 2007-11-06
Hello
Strange that no one has answerd this post in almost a year.
If u still have problem with horde put this in your apache-conf :

> Alias /horde3 /usr/share/horde3
<Directory /usr/share/horde3>
    Options FollowSymLinks
    AllowOverride Limit
    deny from all
    allow from YOUR_IP
</Directory>

Personally I commented out "deny from all" and putted "allow from all"
Change ownership of your php-files to your apache-user.

> # chgrp www-data /etc/horde
# chmod 750 /etc/horde

Restart apache

Now if you enter [http://YOUR_SERVER_IP/horde3](http://YOUR_SERVER_IP/horde3) you would see your unfinished horde-site.

---

### Post by noelcal on 2007-11-08
> **trac said:**
> Hello
Strange that no one has answerd this post in almost a year.
If u still have problem with horde put this in your apache-conf :



Personally I commented out "deny from all" and putted "allow from all"
Change ownership of your php-files to your apache-user.



Restart apache

Now if you enter [http://YOUR_SERVER_IP/horde3](http://YOUR_SERVER_IP/horde3) you would see your unfinished horde-site.

Hi,

 Ihave installed horde3 package on ubuntu 7.04 and also php5 in apache2 , but when i  point my browser at [http://YOUR_SERVER_IP/horde3](http://YOUR_SERVER_IP/horde3) i just get the horde3 code and not the horde-site. It does not interpret. Please help

Thanks

---

### Post by otaviofcs on 2007-12-05
maybe you haven't installed php5 package. I don't know if horde force php instalation (as a dependent package), but it should. Or maybe your apache is not configured to send .php pages to the php interpreter (the php module might not have been loaded).

hope it helps...

---

