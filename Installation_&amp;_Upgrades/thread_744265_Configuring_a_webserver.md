---
title: "Configuring a webserver"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by Diana Rogger on 2008-04-03
Hi,

I have a ADSL connection and I am now configuring a webserver to do advertising and webhosting on my webserver  but I have some questions.

My ISP asked me which ports they must open for me but I don't know which one yet.

Questions:

1) Which ports are open on a webserver?

By default after you installed the webserver you can put your files in to /var/www/


2) Do I have to disable the default server if I am going to use virtual hosts?


Thank you in advanced.


Diana

---

### Post by Oldsoldier2003 on 2008-04-04
> **Diana Rogger said:**
> Hi,

I have a ADSL connection and I am now configuring a webserver to do advertising and webhosting on my webserver  but I have some questions.

My ISP asked me which ports they must open for me but I don't know which one yet.

Questions:

1) Which ports are open on a webserver?

By default after you installed the webserver you can put your files in to /var/www/


2) Do I have to disable the default server if I am going to use virtual hosts?


Thank you in advanced.


Diana

Assuming all you want to run is a webserver:

1) 80 for http if you plan on uploading from a remote site you'll want to open 22 or configure ssh on an alternate port ans have them open that. do not use ftp or telnet because they are insecure protocols, they send usenrname and passwords in the clear.

2) Just edit the default.  /etc/apache2/sites-available/default  example:
```
chuck@ubuntu:~$ cat /etc/apache2/sites-available/default
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/username/public_html/
	<Directory />
		Options FollowSymLinks
		#AllowOverride None
		AllowOverride All
	</Directory>
	<Directory /home/username/public_html/logs/>
		Options Indexes
		AllowOverride All
		Order allow,deny
		allow from all
		
	</Directory>
	<Directory /home/username/public_html/images/>
		AllowOverride all
		Order allow,deny
		allow from all

	</Directory>
        <Directory /home/username/public_html/includes/>
                AllowOverride all
                Order allow,deny
                allow from all

        </Directory>

	

	ScriptAlias /cgi-bin/ /home/username/public_html/cgi-bin/
	<Directory "/home/username/public_html/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

---

