---
title: "PHP not working in Apache2 after updrage to 22.04"
date: 2022-08-27
forum: Installation &amp; Upgrades
---

### Post by novass.net on 2022-08-27
So I took the plunge and updated to 22.04 today.  It went mostly smoothly.  But I found that when I tried to use PHP on my local Apache2 server, it would not execute the code, only display it as text.  I proceeded to mess around with reinstalling apache2, libapache2-mod-php and anything else I could find that is related to the issue.  The actual module seems to be missing, and now I'm stuck in a situation where every time I use apt I'm getting errors related to libapache2-mod-php.

Setting up libapache2-mod-php8.1 (8.1.2-1ubuntu2.3) ...
dpkg: error processing package libapache2-mod-php8.1 (--configure):
 installed libapache2-mod-php8.1 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libapache2-mod-php:
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libapache2-mod-php8.1 (8.1.2-1ubuntu2.3) ...
dpkg: error processing package libapache2-mod-php8.1 (--configure):
 installed libapache2-mod-php8.1 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libapache2-mod-php:
 libapache2-mod-php depends on libapache2-mod-php8.1; however:
  Package libapache2-mod-php8.1 is not configured yet.
Setting up libapache2-mod-php8.1 (8.1.2-1ubuntu2.3) ...
dpkg: error processing package libapache2-mod-php8.1 (--configure):
 installed libapache2-mod-php8.1 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libapache2-mod-php:
 libapache2-mod-php depends on libapache2-mod-php8.1; however:
  Package libapache2-mod-php8.1 is not configured yet.


dpkg: error processing package libapache2-mod-php (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                           Processing triggers for man-db (2.10.2-1) ...
Processing triggers for ufw (0.36.1-4build1) ...
Errors were encountered while processing:
 libapache2-mod-php8.1

 libapache2-mod-php
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm really a bit of an amateur at this, I realize.  But can someone tell me a simple fix here?  Every instruction I can find involves installing these packages, which is now failing.  I just want to fix it without having to nuke my entire ubuntu install and start over.  I really don't have time for this.  I just want it to work, like it did yesterday before I "upgraded."  At least this time it didn't break pihole like the 18-20 upgrade, but I can't run the admin panel until I get this sorted.  I'm probably just being stupid.

---

### Post by MickSulley on 2022-08-28
I had similar problems.  Lots of research, trial and error testing and it is now working again.  
It seems that the OS upgrade also upgrades PHP from 7.4 to 8.1 but links to php8.1 are missing, so I manually added links
    /etc/apache2/mods-enabled/php8.1.conf    > /etc/apache2/mods-available/php8.1.conf
    /etc/apache2/mods-enabled/php8.1.load     >     /etc/apache2/mods-available/php8.1.load 
I don't know why there were not created automatically during the upgrade??

The other issue I had was that I had a file with the line -
    error_reporting(E_ALL|E_STRCT);
and it just stopped, no error message, nothing.  Comment that out and it runs.  I don't understand why!
From what I have seen I thing that PHP8 reports all errors by default

Hope that helps, and if anyone can explain this I would love to know.
Cheers
Mick
ps need to restart Apache or reboot as well

---

### Post by novass.net on 2022-08-31
I think thats on the right track, but I am missing those module files entirely.  I've tried to reinstall the package but it seems to fail, either with an error as in the original post, or is reports no error but the files are not present.  When I run a2enmod, no php module is listed as being available.

---

