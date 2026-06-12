---
title: "Need help with Apache"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by pk_rulz on 2008-02-20
Hi 

I installed Apache 2 by building it with the source. and installed php5 from the repo

I started Apache and saw the happy "It works" webpage

But now I dont know whats happening ... even if I change that page i cant see the changes in browser.

I have cleared the browser's cache  and restarted Apache 10 times  

Please help


Thanks
PK

---

### Post by lsmobrian on 2008-02-20
What file are you editing

/var/www/   should be your root directory for apache

did u create an index.html in that directory

---

### Post by pk_rulz on 2008-02-20
Nope

I am editing /usr/bin/apache2/httpd/index.html I think 

Dont remember the path exactly

---

### Post by lsmobrian on 2008-02-20
In your apache2 configuration directory, least using apt-get install apache2 is /etc/apache2

look for /etc/apache2/sites-available/default

it lists the "DocumentRoot"

if you put an index.html in that directory it should overide the "Welcome to Apache, configure please" site


I didnt install from source, but hopefully its similar



edit:

i have: (same html)
/var/www/index.html
/usr/share/apache2/default-site/index.html  

changes to /var/www/index.html are noticed, /urs/share/...../index.html  are not

---

