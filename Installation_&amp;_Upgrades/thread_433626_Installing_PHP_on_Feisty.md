---
title: "Installing PHP on Feisty"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Janneman_robinson on 2007-05-05
hello,

I've followed the instruction of the unofficial Guideline to install php on my apache webserver.
These we're the instructions:

sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart

After I did that, I've tested the installation with a testphp.php with the instruction phpinfo () ;
When I visited the site [http://localhost/testphp.php](http://localhost/testphp.php), I was asked to download the file.
In the instruction they said the following :
sudo a2enmod php5
sudo /etc/init.d/apache2 force-reload


with the first command, I've got the message:
This module is already enabled!


After this, still the same problem. what am I doing wrong?

---

### Post by czarbal on 2007-05-06
I am also experiencing the same problem. Spent hours on various forums and tried all sorts of suggestions. In all cases I get the same error "Module already enabled". 
/var/www/testphp.php just won't work. I get the "open file with" dialog box when I type [http://localhost/testphp.php](http://localhost/testphp.php)

Details:

ubuntu feisty (7.04)
Apache2
php5
Firefox 2.0.0.3

Thanking you in advance for your help.

Regards,
Chris

---

### Post by czarbal on 2007-05-09
Finally got the damn thing working by adding the following lines to my httpd.conf file. Stopped  apache2 and restarted it and to my astonishment it worked!

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddHandler php5-script php
DirectoryIndex index.html index.php
AddType text/html php
AddType application/x-httpd-php-source phps

Good luck folks.

Cheers,
Chris

---

