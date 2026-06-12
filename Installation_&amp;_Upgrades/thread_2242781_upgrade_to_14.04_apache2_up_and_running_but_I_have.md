---
title: "upgrade to 14.04 apache2 up and running but I have opened the site too much"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by btodd012 on 2014-09-04
Hi help - 
After upgrading to apache2 2.47 I tried to get my site up and succeeded. However, I can now access things that I only want to access from localhost. 

In all my changes, I'm not sure what I did wrong.
I have the default apache2.conf

Here is the Directory stuff in apache2.conf

<Directory />
        Options FollowSymLinks
        AllowOverride None
        Require all denied
</Directory>


<Directory /usr/share>
        AllowOverride None
        Require all granted
</Directory>


<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>


IncludeOptional conf-enabled/*.conf
IncludeOptional sites-enabled/*.conf

In conf-enabled httpd.conf
<Directory />
    Options FollowSymLinks
    AllowOverride None
#   Order deny,allow
#   Deny from all
#   New follows
    Require all denied
    Allow from 127.0.0.1
</Directory>

<Directory /var/www/>
    DirectoryIndex index.php index.html
    AddType text/html .php
    Options Includes Indexes IncludesNoExec FollowSymLinks MultiViews
    XBitHack on
#   Order allow,deny
#   allow from all
    Require all granted
</Directory>



I have the default phpmyadmin.conf 

I can access all directories in /var/www/html
**Problems**
I can access phpmyadmin from the internet not from localhost only...
phpmyadmin.conf has the following

......


# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>


# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>



and **FINALLY**
If there is no index.html or index.php then a directory listing is provided that you can follow.


I have found lots of information - too much - and am having difficulty getting it right...

---

### Post by btodd012 on 2014-09-06
simplifying .... hoping to get some help...

I am trying to prevent access to phpmyadmin from the Internet 

Digital Oceans had some good tutorials and I got farther. I was able prevent access by adding an htaccess file and force authentication. However - I would really like to just prevent access form anywhere but localhost.

I prevented Internet access but I can't enable access from localhost???
Erorr log msg below.
[client 127.0.0.1:52821] AH01630: client denied by server configuration: /usr/share/phpmyadmin/index.php
 
I have a vanilla apache2.conf
virtual host is default also.

I changed the following block in phpmyadmin.conf

<Directory /usr/share/phpmyadmin>
        Options FollowSymLinks
        DirectoryIndex index.php
        <IfModule mod_php5.c>
                AddType application/x-httpd-php .php
                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_admin_flag allow_url_fopen Off
                php_value include_path .
                php_admin_value upload_tmp_dir /var/lib/phpmyadmin/tmp
                php_admin_value open_basedir /usr/share/phpmyadmin/:/etc/phpmyadmin/:/var/lib/phpmyadmin/:/usr/share/php/php-gettext/:/usr/share/javascript/
        </IfModule>


I added the following 3 lines (tried the first 2 first then all 3)
        Require all denied
        Allow from 127.0.0.0/255.0.0.0 ::1/128
        Allow from localhost

</Directory>


I  would have thought that this would have fixed it - seems the deny works but the allow(s) don't.


I do have an httpd.conf also

Here it is without comment lines


ExtendedStatus On
ServerName localhost
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Require all denied
    Allow from 127.0.0.1
</Directory>

<Directory /var/www/>
    DirectoryIndex index.php index.html
    AddType text/html .php
    Options Includes Indexes IncludesNoExec FollowSymLinks MultiViews
    XBitHack on
    Require all granted
</Directory>

<Location />
    Options +Includes
    AddType text/html .shtml
    AddOutputFilter INCLUDES .html
    AddOutputFilter INCLUDES .shtml
</Location>

<Location /server-status>
   SetHandler server-status
   Require all denied
   Allow from 127.0.0.1

I am stumped and going around in circles...
any help would be really appreciated

thanks

---

### Post by btodd012 on 2014-09-10
Hope this helps somebody....
Am surprised nobody could help..

**Summary** - **trying to secure phpmyadmin to localhost or addresses on my local network**

my phpmyadmin.conf in conf-enabled is:

Alias /phpmyadmin /usr/share/phpmyadmin


<Directory /usr/share/phpmyadmin>
        Options FollowSymLinks
        DirectoryIndex index.php
        <IfModule mod_php5.c>
                AddType application/x-httpd-php .php
                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_admin_flag allow_url_fopen Off
                php_value include_path .
                php_admin_value upload_tmp_dir /var/lib/phpmyadmin/tmp
                php_admin_value open_basedir /usr/share/phpmyadmin/:/etc/phpmyadmin/:/var/lib/phpmyadmin/:/usr/share/php/php-gettext/:/usr/share/javascript/
        </IfModule>

        #Require all denied
        #Allow from 192.168.10   --- failed
        #Allow from 127.0.0.0/255.0.0.0 ::1/128    --- failed
        #Allow from localhost --- failed
        #Require host 127.0.0.0/255.0.0.0 ::1/128  --- failed
        Require ip 192.168.10
        Require host localhost
        #Require local
</Directory>


# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>


# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>

[B]SOLUTION:
[/B]You can see in the lines commented out above
        #Require all denied
this blocks everyone
        #Allow from 192.168.10   --- failed
        #Allow from 127.0.0.0/255.0.0.0 ::1/128    --- failed
        #Allow from localhost --- failed
        #Require host 127.0.0.0/255.0.0.0 ::1/128  --- failed
these above all failed after the require all denied. I think the problem was the Require all denied is the new syntax and after that, you cannot allow (I think).
  
From apache 2.4 notes it looks like the require statements below imply deny all except this ip,host or local
      Require ip 192.168.10
        Require host localhost
        #Require local
I think Require local and require host localhost are equivalent (but may not be).

anyway - the 2 statement block access from everyone except localhost on localhost or anybody on the local network that that connect with
[http://192.168.10.xx/phpmyadmin](http://192.168.10.xx/phpmyadmin)

..so .. success

---

