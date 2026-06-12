---
title: "nginx won't start after upgrade to 14.04.5 LTS"
date: 2018-03-29
forum: Installation &amp; Upgrades
---

### Post by chuck4 on 2018-03-29
Upgraded from Ubuntu 12.04.4 LTS to 14.04.5 LTS 

An old Dell GX280 (32-bit) has been running as a web server for a very small site since 2013.  I kept the updates current for a year or so but then I forgot the password and couldn't get into it.  BUT it ran and ran and ran and never had any trouble.  If the power went off, the computer rebooted when the power was restored and within moments the website was up and running.

A few days ago I remembered the password and logged in and was informed that there were hundreds of packages that should be updated and that a new LTS version was available, 14.04.1 LTS.  So I did all that and the result was 14.04.5 LTS which boots and seems to run with only ONE MAJOR problem.

I had installed on the original setup    nginx-1.5.4 and configured it and it operated properly for almost five years.

The current installation included      nginx-1.4.6 which will not start as a service.

#nginx -v -t    reports:
nginx version: nginx/1.4.6 (Ubuntu)
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful


#service nginx start    reports:
Starting nginx: /usr/local/nginx-1.5.4/sbin/nginx: error while loading shared libraries: libgd.so.2: cannot open shared object file: No such file or directory

I say that I have looked "everywhere" for libgd.so.2  but I cannot find it or how to install it.

From another computer, I use a browser to visit the website url and receive the following:
502 Bad Gateway
nginx/1.4.6 (Ubuntu)

=================
Can anyone provide some guidance here?

---

