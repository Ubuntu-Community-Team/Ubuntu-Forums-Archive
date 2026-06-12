---
title: "settings for apache2"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by vatonerd on 2008-03-31
I need help with apache2 configuration. I changed owner of the /var/www folder and files and now my browser gives me a 500 error.

I checked the apache2.conf file and saw tthe the user and group is set for www-data. I chowned the /var/www folder to www-data. Didn't work.

I then chmod the folder www to 755 and the files in the folder to 644. Still doesn't work.

So, I am out of ideas the owner and permissions are getting me confused. I have a running website at //servername/~username. 

What is going on here. Can anyone untangle this for me?

---

### Post by Oldsoldier2003 on 2008-04-02
> **vatonerd said:**
> I need help with apache2 configuration. I changed owner of the /var/www folder and files and now my browser gives me a 500 error.

I checked the apache2.conf file and saw tthe the user and group is set for www-data. I chowned the /var/www folder to www-data. Didn't work.

I then chmod the folder www to 755 and the files in the folder to 644. Still doesn't work.

So, I am out of ideas the owner and permissions are getting me confused. I have a running website at //servername/~username. 

What is going on here. Can anyone untangle this for me?

drwxr-xr-x  3 root root  4096 2008-01-09 15:40 www
```

chown root:root /var/www
chmod 755 /var/www
```

usually I set the site in a user folder and edit the conf to point the web root to said folder.

---

### Post by Oldsoldier2003 on 2008-04-02
example:
/etc/apache2/sites-available/default
```

<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/user/public_html/
	<Directory />
		Options FollowSymLinks
		#AllowOverride None
		AllowOverride All
	</Directory>
	<Directory /home/user/public_html/logs/>
		Options Indexes
		AllowOverride All
		Order allow,deny
		allow from all
		
	</Directory>
	<Directory /home/user/public_html/images/>
		AllowOverride all
		Order allow,deny
		allow from all

	</Directory>


	ScriptAlias /cgi-bin/ /home/user/public_html/cgi-bin/
	<Directory "/home/user/public_html/cgi-bin">
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

