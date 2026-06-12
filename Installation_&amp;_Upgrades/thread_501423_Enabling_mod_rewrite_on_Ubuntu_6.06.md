---
title: "Enabling mod_rewrite on Ubuntu 6.06"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by veletron on 2007-07-15
Hi

I am trying to get apache2 to load mod_rewrite with no success. I have done the following:

sudo a2enmod rewrite

/etc/init.d/apache2 reload

If i look in /etc/apache2/mods-enabled I see rewrite.load

If I enter: sudo apache2ctl -l to list the modules, mod_rewrite is not listed.

Additionally, gallery 1.56 installer is telling me that mod_rewrite is not loaded

Any idea how I can force apache to load mod_re-write. I also tried:

LoadModule mod_rewrite /usr/lib/apache2/modules/mod_rewrite.so in httpd.conf as suggested in another thread, but this gave an error on starting apache:

'Syntax error on line 7 of /etc/apache2/httpd.conf:
Can't locate API module structure `mod_rewrite' in file /usr/lib/apache2/modules/mod_rewrite.so: /usr/lib/apache2/modules/mod_rewrite.so: undefined symbol: mod_rewrite'

The error comes despite the fast that the path to mod_rewrite is the correct path.

I am having other issues installing Gallery 1.56 also (for which I shall make a separate post). Gallery install worked out of the box on my old Mandrake server...

I dont want to use apt-get install gallery because I need multiple installations of gallery for different websites and I keep all my sites in users home dirs under public_html rather than /var/www

The error in gallery setup is: 'Either mod_rewrite is not installed or your .htaccess file is not enabled (see above). Either way, we'll have to use longer URLs in the Gallery. If you want to turn it on, first make sure that your .htaccess file is being obeyed. If it still doesn't work, you may need to reconfigure and rebuild'

I have put  the following in my sites' entry in sites-enabled:

'<Directory /home/veletron/public_html>
        AllowOverride All
</Directory>'

As such, directives in my .htaccess file for this site should be processed.

Anyone got any ideas?

Nigel

---

### Post by Tripmonkey_uk on 2007-07-15
This works on **Dapper**, but I've not tied it on any other versions.

Enable the rewrite module..
[INDENT]sudo a2enmod rewrite[/INDENT]

Open the config file..
[INDENT]sudo nano /etc/apache2/sites-available/default[/INDENT]

Find the following lines..
[INDENT]Options Indexes FollowSymLinks MultiViews
AllowOverride **None** 
Order allow,deny
allow from all[/INDENT]

Change **None** to **all** & save + close the file.

Restart Apache..
[INDENT]sudo /etc/init.d/apache2 restart[/INDENT]

Hope that helps :)

---

### Post by mayhemt on 2007-07-17
Wow this worked like a charm for my wordpress server...thanks a bunch pal..

---

### Post by Tripmonkey_uk on 2007-07-18
No probs chief :)

With all the software that needs that changing before it works, I'm really surprised that the Ubuntu Server doesn't set it by default.

---

