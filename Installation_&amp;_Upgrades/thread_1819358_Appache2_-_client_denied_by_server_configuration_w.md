---
title: "Appache2 - client denied by server configuration when using dynamic ip for access"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by simpoon on 2011-08-06
I have installed moodle on Ubuntu 11. Everything is OK when worked as Intranet. Recently, I wanted to provide the service to the public using dynamic ip. However, the system always returns error Page 403 Forbidden. In the errorlog file the following error was found.

[Sat Aug 06 12:38:23 2011] [error] [client 192.168.1.98] client denied by server configuration: /media/LinExt3/www/moodle/

My config file in sites-available directory is as follows

<VirtualHost *:80>
    ServerAdmin [EMAIL="simpoon8@hotmail.com"]simxxxx@hotmail.com[/EMAIL]
    ServerName vlearners.sytes.net
    ServerAlias *.vlearners.sytes.net
    DocumentRoot /media/LinExt3/www/moodle/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
        allow from all
    </Directory>
    <Directory /media/LinExt3/www/moodle/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    #ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    ScriptAlias /cgi-bin/ /media/LinExt3/www/cgi-bin/
    <Directory "/media/LinExt3/www/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    #ErrorLog ${APACHE_LOG_DIR}/error.log
    ErrorLog /media/LinExt3/www/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    #CustomLog ${APACHE_LOG_DIR}/access.log combined
    CustomLog /media/LinExt3/www/access.log combined
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

The file permission for moodle directory is as follows\
drwxrwsr-x 34 www-data www-data    4096 2011-07-21 23:39 moodle

Appreciate someone can help me to resolve the problem

Thanks in advance

Simpoon :(

---

