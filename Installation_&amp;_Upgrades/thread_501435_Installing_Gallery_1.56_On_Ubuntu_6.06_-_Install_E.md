---
title: "Installing Gallery 1.56 On Ubuntu 6.06 - Install Errors"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by veletron on 2007-07-15
Hi

I am trying to get Gallery 1.56 running on Ubuntu with no luck. It is giving me warnings for 2 things that I need.

One of the errors (about not being able to find mod_rewrite) is dealt with in another post. the error below appears to be because apache is ignoring my .htaccess file. 

"Apache is not obeying the 'php_value' lines in your .htaccess file. Try entering the following into your web server's httpd.conf file:

<Directory /home/veletron/public_html/php/gallery>
	AllowOverride Options FileInfo
</Directory>

If you are running PHP in CGI mode, this message is unavoidable."

So... How do I enable htaccess files (preferably globally and forever, since I use them everywhere in the mandrake install that I am migrating from). I have tried adding the 'AllowOverride ALL'  directive to my sites config file, but this does not work. Likewise, I have uncommented the lines in apache2.conf (search for public_html) to enable .htaccess files for the public_html folders in all my users home directories. (again to no avail). I have restarted apache after making these changes.

Anyone got any ideas? .htaccess was just enabled by default in Mandrake so none of this messing about was nessesary...

Nigel

---

### Post by veletron on 2007-07-15
As am update, I also tried modifying 000-default in sites-enabled and changing all the 'AllowOverride None' to 'AllowOverride All'. After doing this, I restarted apache, but my .htaccess files are still being ignored.

Nigel

---

