---
title: "Apache2 with PHP4"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by cabzzz on 2012-02-03
Hi,

I am trying to find a way to install and configure apache2 along with php4. Apache2 is already installed.

The reason why I want php4 is because I'm working on a project that cannot be upgraded right now, so I have to stick with this old php version. We already have hosted & managed servers that works with that version of php, but I can't speak with them directly. This is to setup a local dev server.

Now, here's what I did :

```
apt-get install flex

wget http://uk.php.net/distributions/php-4.4.9.tar.gz
tar zxf php-4.4.9.tar.gz
cd php-4.4.9/
./configure
make
sudo make install

sudo cp sapi/cli/php /usr/bin/php4
sudo cp sapi/cgi/php /usr/lib/cgi-bin/php4

a2enmod rewrite
sudo a2enmod actions
sudo /etc/init.d/apache2 restart

```

After a reboot, when I type "php -v", it shows me PHP4.4.9 (woohoo!)

But my problem is that is doesn't seem to consider .htaccess correctly. I tried to turn on the option **AllowOverride All**, without any success. And I can confirm the .htaccess is working on hosted servers.

Is there an easier way to install php4, libapache2-mod-php4 with apache2 ? Or is there a way to make sure the .htaccess works.

Sorry if it misses some informations. I'm fairly new to Linux, Apache and PHP, I'm just trying to understand all of that in a really short time.

Thanks to all ! :)

---

### Post by lisati on 2012-02-03
AFAIK, the .htaccess file is used by Apache, not PHP

---

### Post by cabzzz on 2012-02-03
I understand that, but in the .htaccess, there's some line that look like this :

```
php_value log_errors 1
php_value display_errors 0
php_value auto_prepend_file "/some/file.php"
```

Thanks again!

---

### Post by lisati on 2012-02-03
> **cabzzz said:**
> I understand that, but in the .htaccess, there's some line that look like this :

```
php_value log_errors 1
php_value display_errors 0
php_value auto_prepend_file "/some/file.php"
```

Thanks again!

I haven't used anything quite like that myself, so maybe someone else can take a look.

---

### Post by cabzzz on 2012-02-03
Maybe this can help :

This is the /etc/apache2/apache2.conf
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/cabz/htdocs
	<Directory /home/cabz/htdocs>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
	
	AddHandler application/x-httpd-php4 php
	Action application/x-httpd-php4 /cgi-bin/php4
	
	<Files  *.php>
          SetHandler application/x-httpd-php4
    </Files>

</VirtualHost>

```

This is what I get in the /var/log/apache2/error.log :
```
[Fri Feb 03 16:50:30 2012] [alert] [client 10.3.17.90] /home/cabz/htdocs/.htaccess: Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
```

---

### Post by cabzzz on 2012-02-06
After some investigations, I think it is related to the cgi-bin thing.

I guess my apache website is not configured properly. Anyone has an idea on what I should put to enable .htaccess from /cgi-bin/php4 ?

Thanks !

---

