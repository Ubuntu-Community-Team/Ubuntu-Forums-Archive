---
title: "Easy Wordpress install"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-09-22
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

i decided the word press from the repository was improper to install...  this is a quick and dirty how to to get word press running from a sanitary ubuntu install......

alt + f2

gnome-terminal

run

feed the terminal this code...

```

sudo apt-get install mysql-client mysql-server php5 phpmyadmin libapache2-mod-php5

```

set root password for your mysql
set apache2 as your default web server for phpmyadmin

enter root password for database....

then give a different password for phpmyadmin application.

then.....

```

sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin

```

alt + f2

firefox

run

point address in firefox to [http://127.0.0.1/](http://127.0.0.1/) to make sure you get a "it works" to ensure apache is up...  and then [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/) to setup database and users for wordpress.

enter "root" for user, and your password.

then go to

[http://127.0.0.1/phpmyadmin/server_databases.php](http://127.0.0.1/phpmyadmin/server_databases.php)

towards the bottom of the page enter "wordpress" in the blank box, and have it be a collation database on the bottom right, then click create.

on the page that pops up go to privileges then at the bottom of the page hit add user (to add a locked down no permission word press database user)

user name = wordpress
host = local (or external hosts if you so chose)
enter your password for the user word press (generally a good idea to have it as something other than the root database / user password)

and then grant all privileges to the database "wordpress" that you just created.

then leave the global permissions to NOTHING selected (you want this user locked down globally and only to give it access to admin the wordpress database)

then bottom right of the page select GO.....

it will bring up a page asking if you want to give all permissions to the wordpress database.  select "grant" for administration and everything else should automatically be selected already.  this turns on all permissions ON for the wordpress database....  bottom right of database specific settings and hit GO  (notice there is another go button under this, notice, dont click!)

at this point you need to disable phpmyadmin as it is insecure in nature....

to disable your phpmyadmin link @ [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/)

alt + f2

gnome-terminal

run

then drop this block of code
```

sudo rm -rf /etc/phpmyadmin/apache.conf

```
enter sudo password

then immediately run this block of code
```
sudo su
```
and then immediately run this block of code

```

sudo cat > /etc/phpmyadmin/apache.conf << "EOF"
# phpMyAdmin default Apache configuration

# Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
Options FollowSymLinks
DirectoryIndex index.php
<IfModule mod_php5.c>
AddType application/x-httpd-php .php
php_flag magic_quotes_gpc Off
php_flag track_vars On
php_flag register_globals Off
php_value include_path .
</IfModule>
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
EOF
/etc/init.d/apache2 restart
exit

```
and hit enter to exit out of sudo mode, issue another exit to exit the terminal.

to turn [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/) back on

alt + f2

gnome-terminal

run

drop this block of code in the terminal

```

sudo rm -rf /etc/phpmyadmin/apache.conf

```
enter sudo password

then immediately run this block of code
```

sudo su

```
then immediately run this block of code
```

sudo cat > /etc/phpmyadmin/apache.conf << "EOF"
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
Options FollowSymLinks
DirectoryIndex index.php
<IfModule mod_php5.c>
AddType application/x-httpd-php .php
php_flag magic_quotes_gpc Off
php_flag track_vars On
php_flag register_globals Off
php_value include_path .
</IfModule>
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
EOF
/etc/init.d/apache2 restart
exit

```
press enter to exit sudo mode and issue another exit to exit from the terminal.
-------------------------------------------------------------end of unix back end setup-------------------------------------------------------

get the latest wordpress archive.

alt + f2

gnome-terminal

run

then nab this file in your browser

[http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz)

then run this block of code
```

cd $HOME/Downloads/
tar -xf wordpress*.tar.gz
rm -rf wordpress*.tar.gz
sudo mv wordpress /var/www/

```

press enter and then

enter root password

then point your browser @ [http://127.0.0.1/wordpress/](http://127.0.0.1/wordpress/)

you will get a "create a configuration file" dialog to start wordpress installing

click "create a configuration file"

click "lets go"

database name = wordpress
user name = wordpress
password = locked down password given to wordpress user from phpmyadmin
databasehost = local
table prefix = wp_

then hit submit

it should flip out about being ultra locked down, but give a box full of text....

alt + f2

gksu gedit /var/www/wordpress/wp-config.php

run
enter root password
copy text from the browser into the gedit hit save then exit.

{{{{{{SIDE NOTE
use a note pad / something and use this syntax if your using ssh to install this
```

sudo uptime

```
enter pass to unlock sudo
then imediately drop this block of code you have generated in the text editor
```

sudo cat > /var/www/wordpress/wp-config.php << "EOF"
block of code the browser returned that needs to go to wp-config.php
EOF

```
press return
enter
}}}}}

you need to lock down your /var/www/wordpress/wp-config.php file, as is it is showing users the database password...

alt + f2

gnome-terminal

run

then drop this block of code
```

sudo chown www-data /var/www/wordpress/wp-config.php

```
enter root password
then imediately drop this other block of code.
```

sudo chgrp www-data /var/www/wordpress/wp-config.php
sudo chmod 440 /var/www/wordpress/wp-config.php
sudo mkdir /var/www/wordpress/wp-content/uploads
sudo chown www-data /var/www/wordpress/wp-content/uploads/
sudo chgrp www-data /var/www/wordpress/wp-content/uploads/

```

title your site, enter the wordpress admins password / email (deselect having google flocking people to hammer on your site while your at it)

and then click "install wordpress"

user name is "admin"
password is "wordpress admins pass" that you just entered 2 seconds ago.

---

### Post by mörgæs on 2011-09-22
Thanks, but why don't you like installing from a repository?

---

### Post by Dangertux on 2011-09-22
Cool - I didn't even know there was a wordpress repo. Personally I wouldn't use the repo since Wordpress is  updated so frequently, and most of those updates are security related. Updating via the Wordpress dash is just a pain.

---

### Post by boblizar on 2011-09-22
repo places files in obscure directories and is broken by default.  selecting wordpress on synaptic results in 127.0.0.1/wordpress/ not there.  im writing this up because i did not completely finish my wordpress install from a sanitary ubuntu install


i built this tutorial using a sanitary ubuntu virtual machine....  i see my host machine that i originally built the turoial on is out of date.  i update via web interface via wordpresses own management system.  looks like its using a www-data friendly directory.

after using the webupdate i only needed to issue an additional command to further lock down word press.

alt + f2
gnome-terminal
run

```

sudo chmod 440 /var/www/wordpress/wp-config.php
exit

```

---

### Post by Andrew_nuts on 2012-02-21
> **boblizar said:**
> if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

i decided the word press from the repository was improper to install...  this is a quick and dirty how to to get word press running from a sanitary ubuntu install......

alt + f2

gksu synaptic

run

enter your password

search for and install

mysql-client
mysql-server
php5
phpmyadmin

select apply
set root password for your mysql
set apache2 as your default web server for phpmyadmin

enter root password for database....

then give a different password for phpmyadmin application.

then.....

alt + f2

firefox

run

point address in firefox to [http://127.0.0.1/](http://127.0.0.1/) to make sure you get a "it works" to ensure apache is up...  and then [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/) to setup database and users for wordpress.

enter "root" for user, and your password.

then go to

[http://127.0.0.1/phpmyadmin/server_databases.php](http://127.0.0.1/phpmyadmin/server_databases.php)

towards the bottom of the page enter "wordpress" in the blank box, and have it be a collation database on the bottom right, then click create.

on the page that pops up go to privileges then at the bottom of the page hit add user (to add a locked down no permission word press database user)

user name = wordpress
host = local (or external hosts if you so chose)
enter your password for the user word press (generally a good idea to have it as something other than the root database / user password)

and then grant all privileges to the database "wordpress" that you just created.

then leave the global permissions to NOTHING selected (you want this user locked down globally and only to give it access to admin the wordpress database)

then bottom right of the page select GO.....

it will bring up a page asking if you want to give all permissions to the wordpress database.  select "grant" for administration and everything else should automatically be selected already.  this turns on all permissions ON for the wordpress database....  bottom right of database specific settings and hit GO  (notice there is another go button under this, notice, dont click!)

at this point you need to disable phpmyadmin as it is insecure in nature....

to disable your phpmyadmin link @ [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/)

alt + f2

gnome-terminal

run

then drop this block of code
```

sudo rm -rf /etc/phpmyadmin/apache.conf

```
enter sudo password

then immediately run this block of code
```
sudo su
```
and then immediately run this block of code

```

sudo cat > /etc/phpmyadmin/apache.conf << "EOF"
# phpMyAdmin default Apache configuration

# Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
Options FollowSymLinks
DirectoryIndex index.php
<IfModule mod_php5.c>
AddType application/x-httpd-php .php
php_flag magic_quotes_gpc Off
php_flag track_vars On
php_flag register_globals Off
php_value include_path .
</IfModule>
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
EOF
/etc/init.d/apache2 restart
exit

```
and hit enter to exit out of sudo mode, issue another exit to exit the terminal.

to turn [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/) back on

alt + f2

gnome-terminal

run

drop this block of code in the terminal

```

sudo rm -rf /etc/phpmyadmin/apache.conf

```
enter sudo password

then immediately run this block of code
```

sudo su

```
then immediately run this block of code
```

sudo cat > /etc/phpmyadmin/apache.conf << "EOF"
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
Options FollowSymLinks
DirectoryIndex index.php
<IfModule mod_php5.c>
AddType application/x-httpd-php .php
php_flag magic_quotes_gpc Off
php_flag track_vars On
php_flag register_globals Off
php_value include_path .
</IfModule>
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
EOF
/etc/init.d/apache2 restart
exit

```
press enter to exit sudo mode and issue another exit to exit from the terminal.
-------------------------------------------------------------end of unix back end setup-------------------------------------------------------

get the latest wordpress archive.

alt + f2

gnome-terminal

run

then run this block of code
```

cd $HOME/Downloads/
wget http://wordpress.org/latest.tar.gz
tar -xf latest.tar.gz
rm -rf latest.tar.gz
sudo mv wordpress /var/www/

```

press enter and then

enter root password

then point your browser @ [http://127.0.0.1/wordpress/](http://127.0.0.1/wordpress/)

you will get a "create a configuration file" dialog to start wordpress installing

click "create a configuration file"

click "lets go"

database name = wordpress
user name = wordpress
password = locked down password given to wordpress user from phpmyadmin
databasehost = local
table prefix = wp_

then hit submit

it should flip out about being ultra locked down, but give a box full of text....

alt + f2

gksu gedit /var/www/wordpress/wp-config.php

run
enter root password
copy text from the browser into the gedit hit save then exit.

{{{{{{SIDE NOTE
use a note pad / something and use this syntax if your using ssh to install this
```

sudo uptime

```
enter pass to unlock sudo
then imediately drop this block of code you have generated in the text editor
```

sudo cat > /var/www/wordpress/wp-config.php << "EOF"
block of code the browser returned that needs to go to wp-config.php
EOF

```
press return
enter
}}}}}

you need to lock down your /var/www/wordpress/wp-config.php file, as is it is showing users the database password...

alt + f2

gnome-terminal

run

then drop this block of code
```

sudo chown www-data /var/www/wordpress/wp-config.php

```
enter root password
then imediately drop this other block of code.
```

sudo chgrp www-data /var/www/wordpress/wp-config.php
sudo chmod 440 /var/www/wordpress/wp-config.php
sudo mkdir /var/www/wordpress/wp-content/uploads
sudo chown www-data /var/www/wordpress/wp-content/uploads/
sudo chgrp www-data /var/www/wordpress/wp-content/uploads/

```

title your site, enter the wordpress admins password / email (deselect having google flocking people to hammer on your site while your at it)

and then click "install wordpress"

user name is "admin"
password is "wordpress admins pass" that you just entered 2 seconds ago.
Wow ..works great. Tahnks for the tutorial. Only issue is sometime it ask if I have a database connection. But that removes after few refresh. Any suggstion

---

