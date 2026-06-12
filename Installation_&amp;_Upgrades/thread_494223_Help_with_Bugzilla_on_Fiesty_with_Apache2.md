---
title: "Help with Bugzilla on Fiesty with Apache2"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by kju1pitt on 2007-07-06
Hi,  first off thanks for the help ahead of time.  I am very new to ubuntu having come from FC6.  

What I am trying to do is this:

Install and run one copy of bugzilla 3.0 with multiple databases (this is now supported).  

What I have done is to get bugzilla installed,  ubuntu feisty installed with the apache2 and mysql out of the box.

Now bugzilla seems to be ok as far as the perl scripts are concerned.  But what I am running into is I am not at all familar with virtualhosts under ubuntu with apache.  I feel a little lost.

I figure I should be editing some files under /etc/apache2 but I am not sure.

Do I create another site under sites-enabled?  

There is only one ip for this machine.  And only one interface.  So Id like to have one bugzilla running on:

bugzilla.hostname

and the other running on:

internal.hostname

Let me know if you need any other info - this machine is only connected to our local network btw.

I have modified apache2.conf to allow cgi and the default site as follows.

```
NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/


	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

 #   <Directory /var/www/html/bugzilla>
 #   AddHandler cgi-script .cgi
 #   Options +Indexes +ExecCGI
 #   DirectoryIndex index.cgi index.html
 #   AllowOverride ALL
 #   </Directory>
 
</VirtualHost>

<VirtualHost *:80>    

	ServerAdmin webmaster@localhost
	ServerName bugzilla.myhostname

        DocumentRoot /var/www/


    	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

        SetEnv PROJECT main

        Alias /bugzilla /var/www/bugzilla
        <Directory /var/www/html/bugzilla>
           AddHandler cgi-script .cgi
           Options +Indexes +ExecCGI
           DirectoryIndex index.cgi index.html
           AllowOverride ALL
        </Directory>
</VirtualHost>

```

---

### Post by cbciv on 2007-11-19
Check your paths to be sure, but I think that "/var/www/html/bugzilla" should be "/var/www/bugzilla".

Charles

---

