---
title: "Apache fails to start"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by satimis on 2013-01-16
Hi all

OS - Ubuntu 12.04 desktop 64bit running as VM
Virtualizer	Oracle VirtualBox
airtime 2.2.1-1

phpmyadmin NOT installed.

$ sudo service apache2 start```

 * Starting web server apache2
Syntax error on line 5 of /etc/apache2/sites-enabled/airtime-vhost:
ServerAdmin takes one argument, The email address of the server administrator
Action 'start' failed.
The Apache error log may have more information.
   ...fail!

```

$ tail /var/log/apache2/error.log ```

[Wed Jan 16 15:26:06 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Wed Jan 16 15:26:07 2013] [notice] caught SIGTERM, shutting down
[Wed Jan 16 15:26:08 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations
[Wed Jan 16 15:34:43 2013] [notice] caught SIGTERM, shutting down

```

Please advise where to check and how to fix the problem?  TIA

B.R.
satimis

---

### Post by mcduck on 2013-01-16
```
Syntax error on line 5 of /etc/apache2/sites-enabled/airtime-vhost:
ServerAdmin takes one argument, The email address of the server administrator
```
Based on that, your site configuration file has an error on line 5. So that's what you should check. Of course you can post the contents of that file here if you want other people to take a look..

---

### Post by satimis on 2013-01-16
> **mcduck said:**
> ```
Syntax error on line 5 of /etc/apache2/sites-enabled/airtime-vhost:
ServerAdmin takes one argument, The email address of the server administrator
```
Based on that, your site configuration file has an error on line 5. So that's what you should check. Of course you can post the contents of that file here if you want other people to take a look..

$ cat /etc/apache2/sites-enabled/airtime-vhost ```

<VirtualHost *:80>
      ServerName icecast.mydomain.com
      #ServerAlias [www.example.com](www.example.com)

      ServerAdmin root@localhost An email address is required for the virtual host configuration.     

      DocumentRoot /usr/share/airtime/public
      DirectoryIndex index.php

      SetEnv APPLICATION_ENV "production"

      <Directory /usr/share/airtime/public>
              Options -Indexes FollowSymLinks MultiViews
              AllowOverride All
              Order allow,deny
              Allow from all
      </Directory>
</VirtualHost> 

```

line 5 - original```

ServerAdmin root@localhost An email address is required for the virtual host configuration.
```

Tried;
1)
[email]satimis@icecast.mydomain.com[/email]
2)
[email]satimis@mydomain.com[/email]

Also tried;
ServerName [www.mydomain.com](www.mydomain.com)

[email]satimis@mydomain.com[/email] (mail address)

All failed.

Apache2 was automatically installed when running;```

$ sudo apt-get install airtime

```

I suspect there is another config file its content must be matched.

Must "hostname" be matched?

$ hostname```

ub1204dk02
```

$ hostname -f```

ub1204dk02

```

Thanks

satimis

---

### Post by mcduck on 2013-01-16
Just change this:
```
ServerAdmin root@localhost An email address is required for the virtual host configuration.
```
...into this:
```
ServerAdmin root@localhost
```
The rest of the text on the line doesn't belong there and result in the error about the ServerAdmin option only accepting one parameter (having all the other words on the same line would make each word a new parameter for the option. And of course none of the words would be a valid parameter even if the option accepted more than one...

---

### Post by satimis on 2013-01-17
> **mcduck said:**
> Just change this:
```
ServerAdmin root@localhost An email address is required for the virtual host configuration.
```
...into this:
```
ServerAdmin root@localhost
```
The rest of the text on the line doesn't belong there and result in the error about the ServerAdmin option only accepting one parameter (having all the other words on the same line would make each word a new parameter for the option. And of course none of the words would be a valid parameter even if the option accepted more than one...
Hi,

Thanks for your advice.  I got it done

satimis

---

