---
title: "Apache 2 Install on Edgy"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by Deathmoon on 2006-12-01
These forums have been great, however I've ran into an issue and I haven't found the fix yet.  

Here it goes:
I have Edgy running on a box that I want to get Apache 2 running on.  I've installed apache2 and php5 via (sudo aptitude ***).

I know that Apache is running because when I do a sudo /etc/init.d/apache2 stop / start; it gives feedback stating it's stopping (doesn't provide feedback that it is starting - I'm assuming that's normal).

When I try to connect via my browser to my IP address or to [http://localhost/](http://localhost/)
I get the typical "Firefox can't establish a connection to the server at localhost" or "Firefox can't establish a connection to the server at 192.168.15.105", when trying via IP.

So, moving on I wanted to test php therefore I did the following (I also put a index.html page in these directories and nothing works):

/var/www/
/var/www/apache2-default/
/usr/share/apache2/default-site/

Finally, I have added the line:
ServerName localhost

to the file in:
/etc/apache2/apache2.conf

still nothing.

One other item...
I have Squid running on this box as my proxy server.

The above comments regarding the firefox error messages occur when the Proxy Service is stopped.  When I start the squid service, I still get the same error message when i navigate to [http://localhost/](http://localhost/) however when I go to [http://192.168.15.105/](http://192.168.15.105/) I get a different message (see attached)

Ok...last piece of info...this box has Edubuntu on it; shouldn't make a difference that I'm aware of but wanted to include that anyway.

Thanks in advance for any help!

---

### Post by vark on 2007-01-13
Hello,

I have apache2 running a few weeks on 6.10.

Saw your post. As long as browsing [http://localhost](http://localhost) or IP does not give a apache web server welcome page, your out of luck!
It does say starting... as it does stopping...

The files in the webserver root do not mean al is wel, server = localhost will not resolve a non started deamon.

Good advice is difficult, try using webmin (webmin.com) as an admin interface with GUI.
Has helped me often when in trouble.

Regards,

vark

---

### Post by LanceM on 2007-01-18
I believe under /etc/apache2/sites-available there is a file named default. If you look at this file there should be a section named DocumentRoot. The path that this gives is where you should put your .html file.

Also to start and stop apache use apache2ctl
```
sudo apache2ctl start
```

---

### Post by seuaniu on 2007-01-18
This is a bit of a shot in the dark, but have you tried turning squid off?  It may be taking "first dibs" on port 80, and apache can't bind to that port.  You could also open up your /etc/apache2/apache2.conf and change the port it runs on to something different.  Restart apache and connect at localhost:port#.

---

