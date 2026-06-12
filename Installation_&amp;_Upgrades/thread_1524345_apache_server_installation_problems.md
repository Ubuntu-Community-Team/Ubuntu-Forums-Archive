---
title: "apache server installation problems"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by Rahul_Nidhi on 2010-07-05
I am trying to install APACHE2 ....but i am facing problems in starting the server after instalaltion...!!!!
On giving the command:
[B]
sudo /etc/init.d/apache2 start[/B]


It is giving the following error:
[B]
* Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Jul 05 12:47:45 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [ OK ][/B]

I will be very grateful if anyone has any suggestions regarding this..!!!!!

---

### Post by phillw on 2010-07-05
Hi,

It is a standard warning if you do not have a named server set up and can be safely ignored, with the default settings your 'server name' will default to localhost```
http://localhost/
```Should give you the default 'It Works' page from /var/www.

Regards,

Phill.

---

### Post by Iowan on 2010-07-05
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") is one (not necessarily the best) solution.
[This]("http://ubuntuforums.org/showthread.php?t=1464766") thread has a couple more ways.

---

