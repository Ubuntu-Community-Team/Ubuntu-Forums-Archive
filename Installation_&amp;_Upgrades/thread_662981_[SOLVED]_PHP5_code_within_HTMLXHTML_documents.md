---
title: "[SOLVED] PHP5 code within HTML/XHTML documents"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by Toolbelt on 2008-01-09
This one is really wierd:

I installed LAMP server on clean install of Kubuntu 7.10 (Gutsy).

The install was very vanilla.  No errors noted.

I changed Apache2 document root to /media/Abraham/01--ACADRC/
I also changed MySQL base directory to /media/Abraham/01--ACADRC/data/
I symlinked phpmyadmin to /media/Abraham/01--ACADRC/php/phpmyadmin/
I installed mediawiki 1.9 and symlinked to /media/Abraham.01--ACADRC/wiki/
I am able to view phpmyadmin properly, able to setup new databases, tables, etc.
I am able to view the mediawiki start page properly
Here is output on bad URL:

Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 Server at home.acadrc.site Port 80

What I cannot do is properly run php scripts inside my html documents

The following line will not display output in firefox/konqueror when placed within index.html:

<?php phpinfo(); ?>

When I run this line:

<?php echo '<p>Hello World</p>';?>

I get the following results when I view the page in Firefox/Konqueror:

Hello World'; ?>

These results show me that PHP is either not being processed/parsed or, if so, only marginally.

---

### Post by Toolbelt on 2008-01-09
I fixed this by the following steps:

kdesudo kate /etc/apache2/php5.conf

I added .html and .htm to the first AddType line so file looks as follows:

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3 .html .htm
  AddType application/x-httpd-php-source .phps
</IfModule>

Then I restarted apache2:

sudo /etc/init.d/apache2 restart

---

### Post by thisllub on 2008-01-09
You might want to do the same for pdfs too if you plan to serve them.

---

