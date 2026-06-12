---
title: "Ubuntu 9.04 - Apache/PHP broken after recent updates"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by ravingmad on 2010-03-26
My PHP got broken after recent updates I applied.

The error I was getting was:
[I] Starting web server apache2
apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory
   ...fail![/I]

When I checked libphp5.so was indeed missing.

What I did to fix it was to simply reinstall the PHP Apache module and then start Apache.
[B]
sudo aptitude install php5 libapache2-mod-php5[/B]

Hope this helps someone who also runs into this problem.

I "think" the problem may have been caused by Webmin as I ran all the package updates from Webmin and not from the console as I normally do. I've never had aproblem with any package updates so I suspect Webmin did not do something correctly.

---

