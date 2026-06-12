---
title: "cannot see my web pages after upgrading to 14.04"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by horatiu2 on 2014-09-08
Hi there. I just upgraded my U server to 14.04.1 LTS. After upgrading the Apache is working but my web pages are no longer visible. The web pages content now are in /var/www.

How can I see my web pages again? thank you

---

### Post by TheFu on 2014-09-08
The version of apache has changed. There is a new setting needed to enable it.  **Require all granted**

---

### Post by lisati on 2014-09-08
I've read elsewhere (citation/link needed) that with 14.04, Apache now looks in /var/www/html

---

### Post by TheFu on 2014-09-08
> **lisati said:**
> I've read elsewhere (citation/link needed) that with 14.04, Apache now looks in /var/www/html

/var/www/ is what the /etc/apache2.conf file says in a fresh 14.04.1 install here.  Don't know what the sites-available/default file says - restored mine from a backup - so it points to where I have that virtualhost pointing (definitely NOT /var).

---

