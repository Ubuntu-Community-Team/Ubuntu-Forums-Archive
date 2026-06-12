---
title: "Pls, help me run phpmyadmin on Ubuntu 7.10"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by vinaso on 2007-11-09
I install phpmyadmin on Ubuntu 7.10 for desktop by command:
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
afer install I config system again but at Browser when run : [www.localhost/phpmyamin/](www.localhost/phpmyamin/) 
Browser have report:
[COLOR="Black"][B]Not Found

The requested URL /phpmyadmin/ was not found on this server.[/B][/COLOR]
 Pls help me:((

---

### Post by ian dobson on 2007-11-09
Hi,

First try [http://localhost](http://localhost) if you see a web page then try [http://localhost/phpmyamin/](http://localhost/phpmyamin/).

If that doesn't work then check if phpmyadmin is installed in your htdocs directory for apache.

If you have problems just post here again.

Regards
Ian Dobson

---

### Post by vinaso on 2007-11-09
Hi,
Thanks for help me.
In My Apache directory haven't directory httpdocs.
Pls, teach reinstall phpmyadmin on Ubuntu for me:)
I'm new member, I studying about Ubuntu, phpmyadmin very importam for my job.
Thanks so much

---

### Post by whitingx on 2007-11-09
It sounds like something has gone wrong during your install process.

Try uninstalling Apache/phpMyAdmin etc and reinstalling everything from scratch using the following as a guide;

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Hope this helps.

---

### Post by Wirf on 2007-11-09
It seams

```
sudo apt-get install phpmyadmin
```

installs phpmyadmin to /usr/share/phpmyadmin without any link or clue to the user where it has been installed. So you could try

```

cd /var/www
ln -s /usr/share/phpmyadmin phpmyadmin

```

I have changed rights to my /var/www, maybe you need to use sudo or change rights before trying this.

---

