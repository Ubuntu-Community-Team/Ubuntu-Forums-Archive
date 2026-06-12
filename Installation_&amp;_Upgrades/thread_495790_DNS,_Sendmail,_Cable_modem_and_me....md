---
title: "DNS, Sendmail, Cable modem and me..."
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by brattonr on 2007-07-08
I have setup a 7.04 sever, installed Gnome Desktop (until I learn my way around the shell) DNS, Sendmail, Joomla, Apache2, MySQL, PHP5 and everything works fine.  But... (always a but..)

When the server boots, it says that my domain can not be reliably resolved and used the private IP address (192.168.1.101) instead.  My sendmail also says the same thing.

My question is since I am using a cable modem and a router, how do I point my domain to the private IP address and have everything recognize it correctly.  I can surf from any computer to my website just fine.

---

### Post by sjnims on 2008-01-21
I'm having a similar issue - I'm using Gutsy, Apache2, php5, mysql, with joomla 1.0.14. I just installed sendmail with:
```
sudo apt-get install sendmail
```
When I go back to my website and try to register a user, it pauses for a while (+/- 2 minutes) then displays a message that says it completed successfully. I check my email and theres no confirmation message.

System specs:
Ubuntu 7.10
PHP5
mysql
joomla 1.0.14
apache2
phpmyadmin
witlessly connected to a linksys router
no ports being forwarded currently

Joomla! mail settings:
Mailer: PHP mailer
Mail from: [email]sjnims@gmail.com[/email]
From Name: site admin
send mail path: /usr/sbin/sendmail
smtp auth: no
smtp user: blank
smtp pass: blank
smtp host: localhost

---

