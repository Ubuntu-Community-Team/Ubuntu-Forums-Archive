---
title: "Edgy and apache2"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by theQmaster on 2007-06-18
Hi,

When I start my apache I get a strange message I never seen before. It's like the worker is not having the right  settings and it does in the httpd.conf

[B]mc@gsi:/var/run/postgresql$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of apache 2.0 web server...                                                               WARNING: Require ThreadsPerChild > 0, setting to 1
WARNING: Require ThreadsPerChild > 0, setting to 1
                                                                                                     [ ok ][/B]

My httpd.conf shows...


[B]
<IfModule worker.c>
ServerLimit 1024
StartServers 2
MaxClients 1024
MinSpareThreads 1024
MaxSpareThreads 1024
ThreadsPerChild 25
ThreadLimit 4000
MaxRequestsPerChild 0
</IfModule>
[/B]

Any idea why's that ? I had the 2.0.53 version before with similar configuration... What do I miss here ?

My best,
Q

---

### Post by theQmaster on 2007-06-18
Anyone ?

> **theQmaster said:**
> Hi,

When I start my apache I get a strange message I never seen before. It's like the worker is not having the right  settings and it does in the httpd.conf

[B]mc@gsi:/var/run/postgresql$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of apache 2.0 web server...                                                               WARNING: Require ThreadsPerChild > 0, setting to 1
WARNING: Require ThreadsPerChild > 0, setting to 1
                                                                                                     [ ok ][/B]

My httpd.conf shows...


[B]
<IfModule worker.c>
ServerLimit 1024
StartServers 2
MaxClients 1024
MinSpareThreads 1024
MaxSpareThreads 1024
ThreadsPerChild 25
ThreadLimit 4000
MaxRequestsPerChild 0
</IfModule>
[/B]

Any idea why's that ? I had the 2.0.53 version before with similar configuration... What do I miss here ?

My best,
Q

---

### Post by theQmaster on 2007-06-19
I found my answer. For some reason apache2.conf has that value comment set to 0 but the line is commented out... It looks that fixed my problem.

---

