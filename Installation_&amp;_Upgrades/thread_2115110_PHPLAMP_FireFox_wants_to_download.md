---
title: "PHP/LAMP FireFox wants to download"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by mbhavaraju on 2013-02-11
Need Help... Installed LAMP. new to Ubuntu and LAMP. Installation went thru fine. test.php works, when I write simple php and try to use it. FireFox wants to download file and open code in editor instead of executing in browser.

Here is the Simple php code that I wrote.
<html>
<body>
<? php
echo "Welcome to PHP language";
?>
</body>
</html>

I am running this code from Ubuntu server. Using Firefox to run this code. Don't know what I am doing wrong.

---

### Post by Doug S on 2013-02-12
What file name extention did you use? Is it one that will be interpreted as being php?
Where was the file located? If the file was in your own public_html directory, then php in user directories needs to be enabled by editing /etc/apache2/mods-available/php5.conf (comments within the file tell you what to do).

---

### Post by mbhavaraju on 2013-02-12
Hi,

Thanks for replying.  I tried both PHP and HTML extension files.

I did made changes to PHP5.CONF file to point to my personal directory for scripts still didn't help.

---

### Post by SeijiSensei on 2013-02-12
Check to make sure the **libapache2-mod-php5** package is installed.

---

### Post by mbhavaraju on 2013-02-16
Installed these packages and still no luck.

---

### Post by steeldriver on 2013-02-16
I don't know if it's your only issue (if I replicate it, the php command  fails to execute - however the browser doesn't attempt to download the  script) but afaik your php opening tag should not have a space in it i.e. it should be **<?php** not **<? php** 

> **mbhavaraju said:**
> 
[COLOR=Red]<? php[/COLOR]
echo "Welcome to PHP language";
?>


Have you looked in the apache2 error log?

```
tail /var/log/apache2/error.log
```

---

### Post by mbhavaraju on 2013-02-16
hi Thanks for responding... This is what is repeated again and again.


mbhavaraju@rajubuntu:~/Raj/phpcode$ ls -alt
total 80
drwxrwxr-x 2 mbhavaraju mbhavaraju 4096 Feb 10 22:14 .
-rwxrwxrwx 1 mbhavaraju mbhavaraju   89 Feb 10 22:14 MyFirstPhp.php
-rwxrwxrwx 1 mbhavaraju mbhavaraju  293 Feb 10 20:53 MyFirstPhp.html
drwxr-xr-x 9 mbhavaraju mbhavaraju 4096 Feb 10 20:33 ..


[Sun Feb 10 21:46:27 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /home/mbhavaraju/Raj/phpcode/MyFirstPhp.html denied
[Sun Feb 10 21:46:27 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Sun Feb 10 21:46:27 2013] [error] mod_log_sql: child spawned but unable to open database link
[Sun Feb 10 21:46:34 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /home/mbhavaraju/Raj/phpcode/MyFirstPhp.html denied
[Sun Feb 10 21:46:41 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /home/mbhavaraju/Raj/phpcode/MyFirstPhp.html denied
[Sun Feb 10 22:39:25 2013] [notice] caught SIGTERM, shutting down
[Mon Feb 11 21:24:15 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Mon Feb 11 21:24:15 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Mon Feb 11 21:24:16 2013] [error] mod_log_sql: child spawned but unable to open database link
[Mon Feb 11 21:24:16 2013] [error] mod_log_sql: child spawned but unable to open database link
[Mon Feb 11 21:24:15 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Mon Feb 11 21:24:15 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.5 with Suhosin-Patch configured -- resuming normal operations
[Mon Feb 11 21:24:16 2013] [error] mod_log_sql: child spawned but unable to open database link
[Mon Feb 11 21:24:15 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Mon Feb 11 21:24:16 2013] [error] mod_log_sql: child spawned but unable to open database link
[Mon Feb 11 21:24:15 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Mon Feb 11 21:24:16 2013] [error] mod_log_sql: child spawned but unable to open database link
[Mon Feb 11 22:41:42 2013] [notice] caught SIGTERM, shutting down

---

### Post by mbhavaraju on 2013-02-16
good think I just figured out is PHP works fine from command line.

mbhavaraju@rajubuntu:~/Raj/phpcode$ php -f MyFirstPhp.php
Welcome to PHP language
mbhavaraju@rajubuntu:~/Raj/phpcode$ 


So this Works( This is in .php file and executing from command line.:
<?php
echo "Welcome to PHP language\n";
?>

This Doesn't Work(This is in .html file and executing from browser):
<html>
<body>
<?php
echo "Welcome Raj to PHP language";
?>
</body>
</html>

---

### Post by Doug S on 2013-02-17
From your OP (Original Post) I never ever would have guessed that your issue is actually a permissions problem.
 
I suggest that you set up your home directory for the default way for apache to use it.
Make a sub-directory called "public_html" and put your files there. Then tell apache that it is O.K. to use the default users public directory:```
sudo a2enmod userdir
sudo service apache2 restart
```The you access via the URL ~yourusername/file.html example: [http://www.mysite.com/~doug/myfile.html](http://www.mysite.com/~doug/myfile.html)

---

### Post by mbhavaraju on 2013-02-17
hi Doug,

Thanks for responding.. I am not able to successfully do a2enmod.  Please see the following commands and info.

mbhavaraju@rajubuntu:~$ cd /home/mbhavaraju/Raj/phpcode
mbhavaraju@rajubuntu:~/Raj/phpcode$ ls -alt 
total 80
drwxrwxr-x 2 mbhavaraju mbhavaraju 4096 Feb 17 18:25 .
-rwxrwxrwx 1 mbhavaraju mbhavaraju  141 Feb 17 18:25 MyFirstPhp.html
-rwxrwxrwx 1 mbhavaraju mbhavaraju  116 Feb 16 21:41 MyFirstPhp.html~
-rwxrwxrwx 1 mbhavaraju mbhavaraju  266 Feb 16 21:30 MyFirstPhp.php
-rwxrwxrwx 1 mbhavaraju mbhavaraju   43 Feb 16 21:19 MyFirstPhp.php~
drwxr-xr-x 9 mbhavaraju mbhavaraju 4096 Feb 10 20:33 ..
-rwxrwxrwx 1 mbhavaraju mbhavaraju  196 Feb 10 19:08 MyFirstPhp.htm
-rwxrwxrwx 1 mbhavaraju mbhavaraju  196 Feb 10 19:06 MyFirstPhp.htm~

mbhavaraju@rajubuntu:~/Raj/phpcode$ sudo a2enmod /home/mbhavaraju/Raj/phpcode/
ERROR: No module found matching /home/mbhavaraju/Raj/phpcode/!

mbhavaraju@rajubuntu:~/Raj/phpcode$ 

mbhavaraju@rajubuntu:~$ cd public_html
mbhavaraju@rajubuntu:~/public_html$ ls -alt
total 68
drwx------ 94 mbhavaraju mbhavaraju 36864 Feb 17 18:12 ..
drwxrwxrwx  2 mbhavaraju mbhavaraju  4096 Feb 10 13:41 .
-rw-rw-r--  1 mbhavaraju mbhavaraju    20 Feb 10 13:41 test.php
-rw-rw-r--  1 mbhavaraju mbhavaraju    33 Feb 10 13:33 index.html

mbhavaraju@rajubuntu:~/public_html$ sudo a2enmod /public_html
ERROR: No module found matching /public_html!

mbhavaraju@rajubuntu:~/public_html$ 

Public_html is having all the rights
drwxrwxrwx  2 mbhavaraju mbhavaraju     4096 Feb 10 13:41 public_html

---

### Post by mbhavaraju on 2013-02-17
BTW, I can run the html code, but cann't run php code inside html code.  and PHP works fine from Command Prompt.

---

### Post by Doug S on 2013-02-17
Do not do:```
mbhavaraju@rajubuntu:~/public_html$ sudo a2enmod /public_html

```Do exactly what I posted. Do:```
sudo a2enmod userdir
sudo service apache2 restart
```The module name is "userdir" and it refers to "public_html"

---

### Post by mbhavaraju on 2013-02-19
Doug,

Thanks for your Reply,  I did same thing as you said.. Still no help.

mbhavaraju@rajubuntu:~$ sudo a2enmod userdir
[sudo] password for mbhavaraju: 
Module userdir already enabled
mbhavaraju@rajubuntu:~$ sudo service apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
mbhavaraju@rajubuntu:~$

---

### Post by mbhavaraju on 2013-02-19
Hi Doug,

I followed this link and also the link that tells us how to comment things in php5.conf from enabled mods.

[http://joycetipping.com/techblog/2010/08/install-apache-on-ubuntu/#permissions](http://joycetipping.com/techblog/2010/08/install-apache-on-ubuntu/#permissions)

Now, if I goto [http://localhost](http://localhost), it is trying to download php or some kind of file that I don't recognize.  But message is saying it is PHTML kind of file.  I think I got into more problems...

---

### Post by Doug S on 2013-02-19
> Now, if I goto [http://localhost](http://localhost), it is ...??? From your previous posts, I would have expected you to be going to [http://localhost/~mbhavaraju/test.php](http://localhost/~mbhavaraju/test.php) .
So lets take a moment and re-synchronize. Post: Your test.php file; The related /var/log/apache2/error.log; The related /var/log/apache2/access.log.

---

### Post by mbhavaraju on 2013-02-20
Hi Doug,

Here is the test.php.

<?php phpinfo(); ?>


/var/log/apache2/error.log:

[Tue Feb 19 21:38:29 2013] [notice] caught SIGTERM, shutting down
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: child spawned but unable to open database link
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: child spawned but unable to open database link
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: child spawned but unable to open database link
[Tue Feb 19 21:38:31 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: child spawned but unable to open database link
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Tue Feb 19 21:38:31 2013] [error] mod_log_sql: child spawned but unable to open database link
[Tue Feb 19 21:44:17 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Tue Feb 19 21:44:17 2013] [error] mod_log_sql: child spawned but unable to open database link
[Tue Feb 19 21:45:24 2013] [error] [client 127.0.0.1] File does not exist: /var/www/MyFirstPhp.html
[Tue Feb 19 21:45:24 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Tue Feb 19 21:45:24 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Tue Feb 19 21:46:28 2013] [error] [client 127.0.0.1] File does not exist: /var/www/MyFirstPhp.html
[Tue Feb 19 21:46:38 2013] [error] [client 127.0.0.1] File does not exist: /var/www/MyFirstPhp.html
[Tue Feb 19 21:52:43 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /~mbhavaraju denied
[Tue Feb 19 21:53:02 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /~mbhavaraju denied
[Tue Feb 19 21:53:45 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /~mbhavaraju denied
[Tue Feb 19 21:54:04 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /~mbhavaraju denied
[Tue Feb 19 21:54:14 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /~mbhavaraju/ denied
[Tue Feb 19 21:56:50 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /~mbhavaraju/ denied
[Tue Feb 19 22:45:10 2013] [notice] caught SIGTERM, shutting down
[Wed Feb 20 19:08:11 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Wed Feb 20 19:08:11 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Wed Feb 20 19:08:12 2013] [error] mod_log_sql: child spawned but unable to open database link
[Wed Feb 20 19:08:11 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Wed Feb 20 19:08:12 2013] [error] mod_log_sql: child spawned but unable to open database link
[Wed Feb 20 19:08:11 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Wed Feb 20 19:08:12 2013] [error] mod_log_sql: child spawned but unable to open database link
[Wed Feb 20 19:08:11 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Wed Feb 20 19:08:12 2013] [error] mod_log_sql: child spawned but unable to open database link
[Wed Feb 20 19:08:11 2013] [error] mod_log_sql: insufficient configuration info to establish database link
[Wed Feb 20 19:08:12 2013] [error] mod_log_sql: child spawned but unable to open database link


/var/log/apache2/access.log:
127.0.0.1 - - [17/Feb/2013:21:41:58 -0600] "GET /public_html/my-file.html HTTP/1.1" 404 507 "http://joycetipping.com/techblog/2010/08/install-apache-on-ubuntu/" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [17/Feb/2013:21:42:06 -0600] "GET /public_html HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [17/Feb/2013:21:44:12 -0600] "GET /public_html/my-file.html HTTP/1.1" 403 510 "http://joycetipping.com/techblog/2010/08/install-apache-on-ubuntu/" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [17/Feb/2013:21:49:32 -0600] "GET /public_html/my-file.html HTTP/1.1" 403 510 "http://joycetipping.com/techblog/2010/08/install-apache-on-ubuntu/" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [17/Feb/2013:21:50:11 -0600] "GET /public_html/MyFirstPhp.html HTTP/1.1" 403 511 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:44:16 -0600] "GET / HTTP/1.1" 200 482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:45:08 -0600] "GET / HTTP/1.1" 200 482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:45:14 -0600] "GET / HTTP/1.1" 200 482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:45:24 -0600] "GET /MyFirstPhp.html HTTP/1.1" 404 502 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:45:24 -0600] "GET /favicon.ico HTTP/1.1" 404 498 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:45:24 -0600] "GET /favicon.ico HTTP/1.1" 404 498 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:46:28 -0600] "GET /MyFirstPhp.html HTTP/1.1" 404 502 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:46:38 -0600] "GET /MyFirstPhp.html HTTP/1.1" 404 502 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:46:48 -0600] "GET / HTTP/1.1" 200 482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:48:32 -0600] "GET / HTTP/1.1" 200 482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:49:46 -0600] "GET / HTTP/1.1" 200 482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:52:43 -0600] "GET /~mbhavaraju HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:53:02 -0600] "GET /~mbhavaraju HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:53:45 -0600] "GET /~mbhavaraju HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:54:04 -0600] "GET /~mbhavaraju HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:54:14 -0600] "GET /~mbhavaraju/ HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:21:56:50 -0600] "GET /~mbhavaraju/ HTTP/1.1" 403 502 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:22:03:00 -0600] "GET / HTTP/1.1" 200 482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
127.0.0.1 - - [19/Feb/2013:22:14:56 -0600] "GET / HTTP/1.1" 200 482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:18.0) Gecko/20100101 Firefox/18.0"
mbhavaraju@rajubuntu:~$ 

Thanks for all your help Doug

---

### Post by mbhavaraju on 2013-02-20
Doug,

Some more information
apache2ctl -M

 mbhavaraju@rajubuntu:~$ apache2ctl -M
/usr/sbin/apache2ctl: 87: ulimit: error setting limit (Operation not permitted)
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 log_sql_module (shared)
 log_sql_mysql_module (shared)
 log_sql_ssl_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 reqtimeout_module (shared)
 setenvif_module (shared)
 status_module (shared)
 suphp_module (shared)
 userdir_module (shared)
Syntax OK
mbhavaraju@rajubuntu:~$ 

mbhavaraju@rajubuntu:~$ a2dismod mod_log_sql
ERROR: Module mod_log_sql does not exist!
mbhavaraju@rajubuntu:~$ 

I did some changes on php.ini  see the differences here from original.
mbhavaraju@rajubuntu:~$ diff /etc/php5/apache2/php.ini /etc/php5/apache2/php.ini~
435,436c435
< ; expose_php = On Raj Commented this
< expose_php = Off
---
> expose_php = On
539,540c538
< ;display_errors = Off Raj Commented this
< display_errors = On
---
> display_errors = Off
551,552c549
< ; display_startup_errors = Off Raj Commented this
< display_startup_errors = On
---
> display_startup_errors = Off
mbhavaraju@rajubuntu:~$ 
mbhavaraju@rajubuntu:/etc/php5/apache2$ sudo mv php.ini php_ini.old
[sudo] password for mbhavaraju: 
mbhavaraju@rajubuntu:/etc/php5/apache2$ sudo mv php.ini~ php.ini
mbhavaraju@rajubuntu:/etc/php5/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                         ... waiting                                                                                                                                     [ OK ]
mbhavaraju@rajubuntu:/etc/php5/apache2$ 

I did latest Ubuntu updates just now
/var/log/apache2/access.log:
127.0.0.1 - - [20/Feb/2013:20:53:38 -0600] "GET / HTTP/1.1" 200 482 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:19.0) Gecko/20100101 Firefox/19.0"

Still no luck... when I run test.php it tries to download php file.

---

### Post by mbhavaraju on 2013-02-20
Hi Doug,

here is my php5.conf.  Confirming if this configuration is correct.

<Directory /usr/share>
</Directory>
#
<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
	SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
	SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    #    <IfModule mod_userdir.c>
    #        <Directory /home/*/public_html>
    #            php_admin_value engine Off
    #        </Directory>
    #    </IfModule>
</IfModule>

<Files *.php>
SetOutputFilter PHP
SetInputFilter PHP
LimitRequestBody 9524288
</Files>
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

---

### Post by mbhavaraju on 2013-02-20
I am sorry... I am sending so many replies on this post to myself seeking for help.  Doug, thanks for all your help.  This is what I found out latest.

In /etc/apache2/sites-enabled,  if I replace DocumentRoot with /home/mbhavaraju/public_html, and samething with <Directory tag> I am geting 403 error.  If I leave it as is pointng to /var/www/, when I got to //localhost it is trying to download php.  Probably you know what this means, I am trying out each and every thing that I come across.

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www>
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

</VirtualHost>

---

### Post by Doug S on 2013-02-21
I have not looked at your postings of various config files. Why not? Because other than the specific changes mentioned in this thread, you shouldn't need any more changes. Important insight is gained from```
[Tue Feb 19 21:54:04 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /~mbhavaraju denied
[Tue Feb 19 21:54:14 2013] [error] [client 127.0.0.1] (13)Permission denied: access to /~mbhavaraju/ denied

```and```
[Tue Feb 19 21:46:28 2013] [error] [client 127.0.0.1] File does not exist: /var/www/MyFirstPhp.html
[Tue Feb 19 21:46:38 2013] [error] [client 127.0.0.1] File does not exist: /var/www/MyFirstPhp.html
```and```
Here is the test.php.
 
<?php phpinfo(); ?>

```and ```
public_html is having all the rights
drwxrwxrwx 2 mbhavaraju mbhavaraju 4096 Feb 10 13:41 public_html
```So, you still have file permissions issues. Note that permissions in above directories also need to be right. Example (and note, I do not use generally accepted permissions settings, it is just an example):```
doug@doug-64:~$ ls -l -d  /home
drwxr-xr-x 3 root root 4096 Oct 12 09:33 /home
doug@doug-64:~$ ls -l -d  /home/doug
drwxr-xr-x 24 doug doug 4096 Feb 21 06:29 /home/doug
doug@doug-64:~$ ls -l -d  /home/doug/public_html
drwxr-xr-x 25 doug doug 4096 Jan 23 06:56 /home/doug/public_html

```O.K. I now realize test.php is not for access by a browser. So I guess your index.html file has your test php code. Rename the file to index.php

---

