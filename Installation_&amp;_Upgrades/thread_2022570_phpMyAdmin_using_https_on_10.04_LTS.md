---
title: "phpMyAdmin using https on 10.04 LTS"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by Nap_BlownApart on 2012-07-11
Hi,

I see that it is possible to setup phpMyAdmin to use https? However solutions that worked for others won't work for me.
I am running Ubuntu 10.04 LTS with LAMP and ISPConfig3.0.4.6. 
Everything appears to be working; mysql, php, ISPConfig, and phpMyAdmin.
I'm accessing ISPConfig through https, so I'm now trying to get phpMyAdmin to do the same, rather than http.

I installed phpMyAdmin as part of a apt-get install command:
```
apt-get install apache2 apache2.2-common apache2-doc apache2-mpm-prefork apache2-utils libexpat1 ssl-cert libapache2-mod-php5 php5 php5-common php5-gd php5-mysql php5-imap phpmyadmin php5-cli php5-cgi libapache2-mod-fcgid apache2-suexec php-pear php-auth php5-mcrypt mcrypt php5-imagick imagemagick libapache2-mod-suphp
```

So apache2 and phpMyAdmin were presumably installed into the normal folders for the Ubuntu 10.04 LTS distribution.  I installed ISPConfig afterwards.  My "phpMyAdmin default Apache configuration" file is located in /etc/apache2/conf.d/phpmyadmin.conf, and it is in its default state.


As I understand it, I need to redirect the http request to https and this can be done using:
```
        RewriteEngine On
        RewriteCond %{HTTPS} off
        RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
```

In some examples I've seen, the redirect code is wrapped inside XML tags as follows:
```
<IfModule mod_rewrite.c>
  <IfModule mod_ssl.c>
    <Location /phpmyadmin>
      RewriteEngine on
      RewriteCond %{HTTPS} off
      RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI}
   </Location>
  </IfModule>
</IfModule>
```

However both these methods cause my browser to return the error:
```
SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)
```

Since I can access ISPConfig through HTTPS, I'm assuming that I can use HTTPS for phpMyAdmin.  Is this the case, or do I need to setup a certificate for 'non-ISPConfig' access?

Some help would be REALLY appreciated.


Thanks,
Nap

---

### Post by Nap_BlownApart on 2012-07-11
Solution:

add the following lines to your /etc/apache2/conf.d/phpmyadmin.conf (to perform the redirect)

```
<IfModule mod_rewrite.c>
  <IfModule mod_ssl.c>
    <Location /phpmyadmin>
      RewriteEngine on
      RewriteCond %{HTTPS} off
      RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI}
   </Location>
  </IfModule>
</IfModule>
```
before the line containing:
```
Alias /phpmyadmin /usr/share/phpmyadmin
```

then issue the command (to enable HTTPS on your apache2 install)
```
a2ensite default-ssl
```
and restart apache2

What I found strange about this problem is that my ISPConfig install was working with HTTPS before I issued the a2ensite command, thus the solution was harder to find.

In my setup, I'm still using the 'snake-oil' keys that are generated during the install, so I got a browser warning about Trusted Sites, but it did work.

Getting a certificate from a recognised authority will fix the Trust warning, and make your visitors feel more comfortable about using your site.

---

