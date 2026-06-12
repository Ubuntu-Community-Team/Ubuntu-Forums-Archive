---
title: "Perl in Apache2"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by flokky on 2008-05-11
I've just installed Ubuntu 8.04 and have installed LAMP which work perfectly.:KS

Now I want to use Perl within Apache2, but I simply can't seem to find how to set it up properly. I've tried adding some directives to the apache2.conf file, but that just results in 'Internal Server Error', even for the PHP apps that were working correctly before this adjustment. :confused:

Directives I've added in /sites-available/default:
[PHP] ScriptAlias /cgi-bin/ /var/www/html/
        <Directory "/var/www/html/">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                AddHandler cgi-script .pl
                Order allow,deny
                Allow from all
        </Directory>
[/PHP]

And in apache2.conf:
[PHP]AddHandler cgi-script .cgi .pl[/PHP]

I've tried installing Perl, but it seems it is already installed.
[PHP]sudo apt-get install perl[/PHP]

When I get an 'Internal Server Error' this is below the page: 
[PHP]Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g mod_perl/2.0.3 Perl/v5.8.8 Server at 192.168.0.100 Port 80[/PHP]

I've Googled around, but can't seem to find a tutorial for the Apache2 webserver nor for the Ubuntu platform.

Is there someone who can direct me in the right way? Thanks!!

---

### Post by Oldsoldier2003 on 2008-05-12
you wont be able to run cgi scripts without enabling cgi
```

sudo a2enmod cgi
``` if that doesn't do it also enable perl  ```
sudo a2enmod perl
```

---

