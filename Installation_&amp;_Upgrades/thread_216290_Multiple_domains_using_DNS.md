---
title: "Multiple domains using DNS?"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by zOdeac on 2006-07-15
Ok I am lost here I though I had a idea to solve my problem but I guess I just don’t know enough yet to understand what I am doing so can some one help me please.

I created 4 users and they all have WebPages example,

Site.com/~user1
Site.com/~user2
Site.com/~user3
Site.com/~user4

Now I want to put domains with each of this users so it will come out like

Site1.com will go to user1
Site2.com will go to user2
Site3.com will go to user3
Site4.com will go to user4

I was under the impression that all I had to do is put a record in to bind9 and away I go boy I was wrong.

Anyone have a how-to on setting this up.  I attempted to do something with VHCS but I got some errors and rebuilt the server again.
Oh and I am running ubuntu 6.06 server.  Also attempting to set this all up with webmin thanks for any help.

---

### Post by zOdeac on 2006-07-15
Never mind i found it for anyone else that looks here is what i did to the apache2.conf file

NameVirtualHost *:80

<VirtualHost *:80>
ServerName website1.com
ServerAlias [www.website1.com](www.website1.com) *.website1.com
ServerAdmin [email]admin@website1.com[/email]
DocumentRoot /var/www/web1
</VirtualHost>

<VirtualHost *:80>
ServerName [www.website2.org](www.website2.org)
ServerAlias website2.org *.website2.org
ServerAdmin [email]admin@website2.org[/email]
DocumentRoot /var/www/web2
</VirtualHost>

---

### Post by CzarAlex on 2006-09-05
Thanks for your update post. This is exactally what I was looking for. I appreciate the time you took to post this info for others to find! :KS :KS

---

